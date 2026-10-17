<p align="center">
  <a href="https://tryhackme.com/">
    <img src="https://assets.tryhackme.com/img/logo/tryhackme_logo_full.svg" alt="TryHackMe" width="300">
  </a>
</p>

# THM Rooms

My walkthroughs and notes for **[TryHackMe](https://tryhackme.com/)**.

I document my own solutions and approaches, showing **what** I did and **how** I did it while working through each room.

## Rooms

| Room | Difficulty | Topics | Walkthrough |
|------|------------|--------|-------------|
| [Agent T](https://tryhackme.com/room/agentt) | Easy | Nmap enumeration, searchsploit, PHP 8.1.0-dev `User-Agentt` backdoor RCE | [Easy/Agent_T/Agent_T.md](Easy/Agent_T/Agent_T.md) |
| [Bounty Hacker](https://tryhackme.com/room/cowboyhacker) | Easy | Anonymous FTP, web enumeration, Hydra brute-force, GTFOBins (tar) privesc | [Easy/Bounty_Hacker/Bounty_Hacker.md](Easy/Bounty_Hacker/Bounty_Hacker.md) |
| [Corridor](https://tryhackme.com/room/corridor) | Easy | IDOR, MD5 hashes, web enumeration | [Easy/Corridor/Corridor.md](Easy/Corridor/Corridor.md) |
| [CyberHeroes](https://tryhackme.com/room/cyberheroes) | Easy | Client-side auth, JS source review, string reversal | [Easy/CyberHeroes/CyberHeroes.md](Easy/CyberHeroes/CyberHeroes.md) |
| [Dig Dug](https://tryhackme.com/room/digdug) | Easy | DNS enumeration, `dig`, TXT records | [Easy/Dig_Dug/Dig_Dug.md](Easy/Dig_Dug/Dig_Dug.md) |
| [Hidden Deep Into my Heart](https://tryhackme.com/room/lafb2026e9) | Easy | `robots.txt` info disclosure, directory brute-forcing (ffuf), default/leaked credentials | [Easy/Deep_Into_my_Heart/Deep_Into_my_Heart.md](Easy/Deep_Into_my_Heart/Deep_Into_my_Heart.md) |
| [Lo-Fi](https://tryhackme.com/room/lofi) | Easy | LFI, path traversal | [Easy/Lo-Fi/Lo-Fi.md](Easy/Lo-Fi/Lo-Fi.md) |
| [Neighbour](https://tryhackme.com/room/neighbour) | Easy | IDOR, web enumeration | [Easy/Neighbour/Neighbour.md](Easy/Neighbour/Neighbour.md) |
| [Silver Platter](https://tryhackme.com/room/silverplatter) | Easy | Web enumeration, CVE-2024-36042 (Silverpeas auth bypass), log-based credential hunting, password reuse, sudo privesc | [Easy/Silver_Platter/Silver_Platter.md](Easy/Silver_Platter/Silver_Platter.md) |
| [Simple CTF](https://tryhackme.com/room/easyctf) | Easy | Nmap, web enumeration, CVE-2019-9053 (CMS Made Simple SQLi), Hydra brute-force, GTFOBins (vim) privesc | [Easy/Simple_CTF/Simple_CTF.md](Easy/Simple_CTF/Simple_CTF.md) |
| [The Sticker Shop](https://tryhackme.com/room/thestickershop) | Easy | Stored XSS, SSRF-via-victim | [Easy/The_Sticker_Shop/The_Sticker_Shop.md](Easy/The_Sticker_Shop/The_Sticker_Shop.md) |
| [Tomghost](https://tryhackme.com/room/tomghost) | Easy | CVE-2020-1938 (Ghostcat), GPG cracking, sudo zip GTFOBins | [Easy/Tomghost/tomghost.md](Easy/Tomghost/tomghost.md) |

## Repository structure

```
THM_Rooms/
├── README.md
└── Easy/
    ├── Agent_T/
    │   ├── Agent_T.md
    │   └── Assets/
    ├── Bounty_Hacker/
    │   ├── Bounty_Hacker.md
    │   └── Assets/
    ├── Corridor/
    │   ├── Corridor.md
    │   └── Assets/
    ├── CyberHeroes/
    │   ├── CyberHeroes.md
    │   └── Assets/
    ├── Deep_Into_my_Heart/
    │   ├── Deep_Into_my_Heart.md
    │   └── Assets/
    ├── Dig_Dug/
    │   ├── Dig_Dug.md
    │   └── Assets/
    ├── Lo-Fi/
    │   ├── Lo-Fi.md
    │   └── Assets/
    ├── Neighbour/
    │   ├── Neighbour.md
    │   └── Assets/
    ├── Silver_Platter/
    │   ├── Silver_Platter.md
    │   └── Assets/
    ├── Simple_CTF/
    │   ├── Simple_CTF.md
    │   └── Assets/
    ├── The_Sticker_Shop/
    │   ├── The_Sticker_Shop.md
    │   └── Assets/
    └── Tomghost/
        ├── tomghost.md
        └── Assets/
```

Rooms are grouped by difficulty (`Easy/`, `Medium/`, `Hard/`, ...), each in its own folder containing the walkthrough and an `Assets/` folder for screenshots.

## Disclaimer

All content in this repository is based on my own work and notes. It is intended for educational purposes only and covers intentionally vulnerable machines provided by TryHackMe.