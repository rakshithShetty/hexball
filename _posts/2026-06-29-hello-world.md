---
layout: post
title: "Why I'm building a hex-grid football game"
date: 2026-06-29
categories: devlog
---

Football is the sport I grew up watching. Chess is the game I kept coming back to in my head — the idea that a sport could work like a puzzle, where every position matters and every resource decision has a cost.

I wanted to see what a football game would look like if you stripped away the reflexes and real-time chaos, and replaced them with the slow, deliberate tension of a turn-based strategy game. Not a football *simulator* — a football *game*, where positioning and reading the opponent are the skills that win.

That idea became HexBall.

---

## Why hex?

The first version used a square grid. It felt wrong immediately. Diagonal movement had this awkward quality — you could skirt around defenders at a weird angle that didn't match how football actually works. Players spread across a pitch in 6 directions, not 4 or 8.

Hexagonal grids give 6 equidistant neighbours. That maps naturally to how a footballer sees space: wide left, wide right, central, forward, back, and the diagonals between. Pass geometry and line-of-sight checks also become much cleaner — there's no "does the diagonal count?" ambiguity.

The moment I switched to hex, the game started feeling like football.

---

## The dice question

The trickiest early design problem was the dice model. Too random and skill doesn't matter; too deterministic and the game becomes solved chess — the better team always wins, nothing interesting happens.

I ran Monte Carlo simulations to find the sweet spot. The target:

- Equal teams → ~50% win rate each
- Elite striker vs average GK → ~30% goal rate (hard to score, but possible)
- Upsets → 5–15% (better team usually wins, but not always)

After comparing 2d6, 3d6, and flat d20 models, **3d6** hit the target distribution best. The bell curve means elite players consistently outperform average ones, but the tails are fat enough that anything can happen on a given day.

---

## Where it is now

I'm calling the current build Sprint 5.7. The core is solid:

- Full 11v11 match engine, config-driven
- All base actions: move, pass, long pass, shoot, tackle
- 5 special abilities (through ball, power shot, slide tackle, sweeper punch, press trigger)
- A reaction system where defenders pre-declare responses before the attacking turn resolves
- Heuristic AI with influence maps and multi-step planning
- Headless batch simulation for balance testing
- 244 passing tests

The renderer runs in pygame — you can watch two AI teams play, or take control of one side yourself.

---

## What's next

The current focus is polishing the AI and expanding the ability system. Longer term I want to explore a proper MCTS planner and eventually see if a trained model can discover non-obvious tactics.

I'll keep posting here as things develop. Next up: a proper look at the reaction system and why it changes the tactical feel of the game entirely.
