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
| [Lo-Fi](https://tryhackme.com/room/lofi) | Easy | LFI, path traversal | [Easy/Lo-Fi/Lo-Fi.md](Easy/Lo-Fi/Lo-Fi.md) |
| [Neighbour](https://tryhackme.com/room/neighbour) | Easy | IDOR, web enumeration | [Easy/Neighbour/Neighbour.md](Easy/Neighbour/Neighbour.md) |
| [The Sticker Shop](https://tryhackme.com/room/thestickershop) | Easy | Stored XSS, SSRF-via-victim | [Easy/The_Sticker_Shop/The_Sticker_Shop.md](Easy/The_Sticker_Shop/The_Sticker_Shop.md) |

## Repository structure

```
THM_Rooms/
├── README.md
└── Easy/
    ├── Corridor/
    │   ├── Corridor.md
    │   └── Assets/
    ├── Lo-Fi/
    │   ├── Lo-Fi.md
    │   └── Assets/
    ├── Neighbour/
    │   ├── Neighbour.md
    │   └── Assets/
    └── The_Sticker_Shop/
        ├── The_Sticker_Shop.md
        └── Assets/
```

Rooms are grouped by difficulty (`Easy/`, `Medium/`, `Hard/`, ...), each in its own folder containing the walkthrough and an `Assets/` folder for screenshots.

## Disclaimer

All content in this repository is based on my own work and notes. It is intended for educational purposes only and covers intentionally vulnerable machines provided by TryHackMe.