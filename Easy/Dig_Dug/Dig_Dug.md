# Dig Dug

![Dig Dug](Assets/Dig_Dug_1.png)

> A tiny, focused room about DNS enumeration — the target machine is a DNS server that only answers one very specific kind of query.

**Task:** find out why the machine only responds to a special request for `givemetheflag.com`, then retrieve the flag.

**Room link:** https://tryhackme.com/room/digdug

---

## 1. Verify the machine is running

```bash
ping -c 3 10.130.168.157
```

- `-c 3` sends exactly 3 ICMP echo requests and then stops, instead of pinging forever.

```
PING 10.130.168.157 (10.130.168.157) 56(84) bytes of data.
64 bytes from 10.130.168.157: icmp_seq=1 ttl=62 time=10.9 ms
64 bytes from 10.130.168.157: icmp_seq=2 ttl=62 time=9.72 ms
64 bytes from 10.130.168.157: icmp_seq=3 ttl=62 time=11.4 ms

--- 10.130.168.157 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 9.719/10.676/11.375/0.700 ms
```

0% packet loss confirms the machine is up and reachable.

## 2. Port scanning with Nmap

```bash
nmap -sC -sV 10.130.168.157
```

- `-sC` runs Nmap's **default script set** (`--script=default`), a collection of safe, non-intrusive NSE scripts that grab extra banner/version/config info (e.g. `ssh-hostkey` below).
- `-sV` enables **version detection**, so Nmap tries to identify the exact product and version behind each open port instead of just naming the service.
- No `-p` is given, so Nmap scans its default list of the 1000 most common TCP ports.

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   3072 8e:65:ef:c8:7e:d2:04:59:ad:9d:8a:af:7c:63:f9:f6 (RSA)
|   256 7d:3d:72:ea:df:cc:2b:09:58:01:82:e3:d4:67:7f:b8 (ECDSA)
|_  256 cc:8f:49:15:31:77:a3:73:f0:0b:f7:37:f2:ce:2a:d3 (ED25519)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

Only port 22 (SSH) shows up as open TCP. That's strange for a room whose brief explicitly talks about a DNS server — DNS normally lives on port 53. The catch is that Nmap's default scan only probes **TCP**, while DNS primarily speaks **UDP**. Since UDP port 53 isn't in Nmap's TCP results, it doesn't mean DNS isn't there; it means we scanned the wrong protocol, so the next step is to go straight at it with a DNS client instead of re-scanning.

## 3. Querying the DNS service with `dig`

`dig` ("domain information groper") is the standard CLI tool for querying DNS servers directly.

```bash
dig 10.130.168.157
```

With no `@server` specified, this just asks our own resolver to look up the name `10.130.168.157` (treating it as a hostname, not a target) — so it's really querying our local DNS, not the box:

```
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 51751
;; QUESTION SECTION:
;10.130.168.157.                        IN      A

;; AUTHORITY SECTION:
.                       5       IN      SOA     a.root-servers.net. nstld.verisign-grs.com. 2026100901 1800 900 604800 86400
```

`NXDOMAIN` confirms there's no such public domain — expected, since we never told `dig` to actually ask *our* target machine anything.

The room's hint says the server only responds to a **special request for a `givemetheflag.com` domain**. Putting that together with `dig`'s syntax:

```bash
dig givemetheflag.com @10.130.168.157
```

- `givemetheflag.com` is the **name** being queried (the question we're asking the DNS server).
- `@10.130.168.157` tells `dig` to send the query **directly to this server**, instead of our default resolver — this is what actually reaches the target machine on UDP/53.

```
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4141
;; flags: qr aa; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;givemetheflag.com.             IN      A

;; ANSWER SECTION:
givemetheflag.com.      0       IN      TXT     "flag{...}"
```

`NOERROR` plus `aa` (authoritative answer) shows the server knows exactly this domain and answers for it directly. Even though `dig` defaults to asking for an `A` record, the server replies with a **TXT** record containing the flag — TXT records are free-form text fields in DNS, commonly used for things like domain verification, SPF, or (here) smuggling out a flag.

## 4. Cleaning up the query

The raw output is verbose. We can ask `dig` explicitly for the `TXT` record type and trim the output to just the answer:

```bash
dig givemetheflag.com @10.130.168.157 TXT +short
```

- `TXT` explicitly requests the TXT record type (rather than relying on the server ignoring our implicit `A` request type).
- `+short` strips out all the header/question/footer noise and prints only the answer data.

```
"flag{...}"
```

Flag retrieved.

---

## Takeaways

- A closed/absent result on a TCP port scan doesn't rule out a service running over **UDP** — DNS (port 53) is a classic example, since Nmap's default `nmap -sC -sV` only probes TCP.
- `dig <name> @<server>` is the key pattern for querying a *specific* DNS server directly instead of your system's default resolver.
- DNS isn't limited to `A`/`AAAA` records: `TXT` records can hold arbitrary data, which makes them a convenient (if unconventional) place to hide a flag.
- `+short` is a handy `dig` flag for scripting or quickly grabbing just the answer without the full diagnostic output.

**Mitigation:** this was an intentionally misconfigured teaching lab (a DNS zone serving a flag in a TXT record), so there's no real-world "fix" beyond the general DNS hygiene point: authoritative DNS servers should only serve records for zones they're meant to be authoritative for, and should not expose arbitrary/sensitive data via TXT records to anyone who asks.