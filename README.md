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
| [Corridor](https://tryhackme.com/room/corridor) | Easy | IDOR, MD5 hashes, web enumeration | [Easy/Corridor/Corridor.md](Easy/Corridor/Corridor.md) |
| [CyberHeroes](https://tryhackme.com/room/cyberheroes) | Easy | Client-side auth, JS source review, string reversal | [Easy/CyberHeroes/CyberHeroes.md](Easy/CyberHeroes/CyberHeroes.md) |
| [Dig Dug](https://tryhackme.com/room/digdug) | Easy | DNS enumeration, `dig`, TXT records | [Easy/Dig_Dug/Dig_Dug.md](Easy/Dig_Dug/Dig_Dug.md) |
| [Lo-Fi](https://tryhackme.com/room/lofi) | Easy | LFI, path traversal | [Easy/Lo-Fi/Lo-Fi.md](Easy/Lo-Fi/Lo-Fi.md) |
| [Neighbour](https://tryhackme.com/room/neighbour) | Easy | IDOR, web enumeration | [Easy/Neighbour/Neighbour.md](Easy/Neighbour/Neighbour.md) |
| [Simple CTF](https://tryhackme.com/room/easyctf) | Easy | Nmap, web enumeration, CVE-2019-9053 (CMS Made Simple SQLi), Hydra brute-force, GTFOBins (vim) privesc | [Easy/Simple_CTF/Simple_CTF.md](Easy/Simple_CTF/Simple_CTF.md) |
| [The Sticker Shop](https://tryhackme.com/room/thestickershop) | Easy | Stored XSS, SSRF-via-victim | [Easy/The_Sticker_Shop/The_Sticker_Shop.md](Easy/The_Sticker_Shop/The_Sticker_Shop.md) |
| [Tomghost](https://tryhackme.com/room/tomghost) | Easy | CVE-2020-1938 (Ghostcat), GPG cracking, sudo zip GTFOBins | [Easy/Tomghost/tomghost.md](Easy/Tomghost/tomghost.md) |

## Repository structure

```
THM_Rooms/
├── README.md
└── Easy/
    ├── Corridor/
    │   ├── Corridor.md
    │   └── Assets/
    ├── CyberHeroes/
    │   ├── CyberHeroes.md
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