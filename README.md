# ₿ The Bitcoin Game

**A free, browser-based classroom simulation of Bitcoin mining and Proof of Work.**

Live at → **[thebitcoingame.io](https://thebitcoingame.io)**

---

## What is it?

The Bitcoin Game is an interactive educational tool that teaches Bitcoin mining, blockchain technology, and the Proof of Work consensus mechanism through competitive classroom gameplay. Students act as miners, competing to find valid hashes, select profitable transactions, and reach consensus — mirroring exactly how the real Bitcoin network operates.

No installation. No accounts. No backend. Opens in any browser in seconds.

---

## Why it exists

Most blockchain courses teach Proof of Work through slides and diagrams. Students understand it intellectually but never *feel* it. This game was built to close that gap — to make the mechanism visceral, competitive, and socially experienced so the understanding sticks.

Built by **Guillermo A. Beuchat**, Professor at Universidad de Chile, Business Consultant, and Blockchain enthusiast.

---

## How to use it

There are two roles:

| Role | File | Who opens it |
|------|------|--------------|
| **Satoshi View** | `BTCsatoshi.html` | The educator / moderator — projected on a shared screen |
| **Miner View** | `BTCminer.html` | Each student — on their own device |

### Running a session

1. The educator opens `BTCsatoshi.html` and projects it on a classroom screen (or shares it via Zoom / Teams for remote sessions)
2. Students open `BTCminer.html` on their own devices — laptop, tablet, or phone
3. The educator sets game parameters (number of miners, block reward, difficulty) and clicks **Initialize**
4. Click **Open New Block** — a countdown runs, 10 transactions appear in the pool, and the mining race begins
5. Students guess nonces in their Hash Calculator until the computed hash meets the difficulty condition, then shout **"BITCOIN!"**
6. The class validates the block together — Satoshi enters the winning nonce, everyone reproduces the hash independently
7. If consensus is reached, the block closes, balances update, and the next block opens
8. After 10 blocks, the miner with the highest BTC balance wins

A full session runs approximately **60–90 minutes**. Shorter sessions of 3–5 blocks run in 30–45 minutes.

---

## What students learn

- **Proof of Work** — the trial-and-error nature of mining becomes physically felt, not just intellectually understood
- **Hash functions** — every nonce change produces a completely different hash; the avalanche effect becomes intuitive
- **Transaction fee strategy** — students discover why miners prioritise high-fee transactions through self-interest
- **Consensus without trust** — the validation phase demonstrates that math, not authority, makes blockchain trustless
- **Blockchain immutability** — each block depends on the previous block's hash; altering history breaks the chain
- **Mining difficulty adjustment** — the educator can change difficulty mid-game, mirroring Bitcoin's 2016-block adjustment
- **51% attack intuition** — the consensus mechanic naturally generates the question: what if miners colluded?

---

## Who it is for

- University professors in business schools, computer science, economics, and fintech programs
- High school teachers running technology or economics electives
- Corporate trainers at fintech firms, banks, and consulting companies
- Blockchain and Web3 bootcamp instructors
- Conference speakers running live interactive workshops

Works in-person and remotely. Supports 2 to 20 players per session.

---

## Technical details

| Property | Detail |
|----------|--------|
| **Stack** | Pure HTML, CSS, JavaScript — no framework, no build system |
| **Backend** | None — entirely client-side |
| **Dependencies** | CryptoJS 4.1.1 (CDN) for MD5 hashing · Google Fonts (Inter + JetBrains Mono) |
| **Persistence** | Browser `localStorage` — game state survives tab close and refresh |
| **Hashing** | Real MD5 cryptographic function — not a simulation |
| **Players** | 2–20 miners per session |
| **Blocks** | 10 blocks per game |
| **Responsive** | Miner View fully responsive (mobile, tablet, desktop) |
| **Offline** | Works offline once loaded |

### File structure

```
index.html          ← Home page / role selector
BTCsatoshi.html     ← Moderator (educator) view
BTCminer.html       ← Player (student) view
BTCbackground.jpg   ← Background image
sitemap.xml         ← Sitemap for search engines
robots.txt          ← Crawler instructions
```

### Key design decisions

**Transaction ordering** — transactions are always concatenated in ascending numerical order (T1T3T7, never T7T3T1) regardless of click order. This ensures every miner computes the same hash for the same block, eliminating a common source of consensus failure.

**DOM-free state** — game state is stored in JavaScript variables, not DOM element text content. The DOM is write-only for display purposes, preventing a class of silent data-corruption bugs.

**Floating-point safety** — all balance arithmetic uses integer rounding (`Math.round(value * 100) / 100`) to prevent BTC balance drift across multiple transactions and blocks.

**Re-entrancy guard** — `openBlock()` sets a `blockIsOpen` flag that prevents double-clicking from generating duplicate transaction sets or running parallel countdown timers.

**End-of-game guard** — all game functions check `currentBlock > MAX_BLOCKS` before executing, preventing crashes after block 10 is closed.

---

## Running locally

No build step required. Clone or download the repository and open `index.html` in any modern browser:

```bash
git clone https://github.com/gabeuchat/thebitcoingame.git
cd thebitcoingame
open index.html   # macOS
# or just double-click index.html in your file explorer
```

Alternatively, serve it with any static file server:

```bash
npx serve .
# then open http://localhost:3000
```

---

## Customisation

The game is designed to be adapted. Key parameters are editable in the Satoshi View before and during the game:

| Parameter | Default | Notes |
|-----------|---------|-------|
| Number of miners | — | 2–20. Remaining slots become fictional users |
| Miner reward | 0.5 BTC | Awarded to the miner who successfully closes each block |
| Max block size | 1000 | Sum of selected transaction sizes must not exceed this |
| Mining difficulty | Ended in 9 | Change the required hash ending at any time mid-game |

To change the number of blocks (default 10), update the `MAX_BLOCKS` constant in `BTCsatoshi.html`.

---

## License

**Copyright free.** Use it, share it, adapt it, translate it. No attribution required, though it is always appreciated.

---

## Support the project

If this tool was useful for your course, you can support its continued development:

[Donate via PayPal](https://paypal.me/guillebeuchat) ☕

---

## Author

**Guillermo A. Beuchat**
Business Consultant · Startup Founder · Professor at Universidad de Chile · Blockchain Enthusiast

[LinkedIn](https://www.linkedin.com/in/guillebeuchat/) · [thebitcoingame.io](https://thebitcoingame.io)

---

## Topics

`bitcoin` `blockchain` `proof-of-work` `education` `classroom` `simulation` `cryptocurrency` `fintech` `edtech` `mining` `consensus` `hash-function` `interactive` `game` `free`
