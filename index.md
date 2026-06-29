---
layout: home
title: HexBall
---

# HexBall

**Turn-based tactical football on a hexagonal grid.**

Two AI-controlled teams of 11 face off on a hex map — moving, passing, shooting, and tackling in alternating turns. Every contested action resolves with 3d6 + player stats, so elite players win more often but upsets happen. A human can jump in at any time via the pygame watch-mode renderer.

The project is a solo dev experiment in building a complete, sim-ready sports engine from scratch: legible rules, deep positioning strategy, and a fully headless batch simulation pipeline for balance analysis.

---

## Screenshots

<!-- Add screenshots below as you have them. Format:
  ![Description](assets/images/your-file.png)
-->

*Screenshots coming soon — check back after the next sprint.*

---

## Key Features

| | |
|---|---|
| **Hex grid tactics** | Axial coordinate system; pathfinding; line-of-sight for passes and shots |
| **Full action set** | MOVE, PASS, LONG PASS, SHOOT, TACKLE, plus 5 special abilities |
| **Reaction system** | Defenders pre-declare responses (GK Dive, Intercept Lane, Jockey, Press) |
| **Heuristic AI** | Influence maps, positional scoring, multi-step lookahead planning |
| **Batch simulation** | Headless N-match runner; JSONL logs; analytics dashboard |
| **Balance-validated** | Dice model locked via Monte Carlo — equal teams ~50% win rate; upsets 5–15% |

---

## Devlog

Check the [Blog](/hexball/blog) for development updates, design decisions, and lessons learned.
