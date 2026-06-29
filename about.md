---
layout: page
title: About
permalink: /about/
---

## What is HexBall?

HexBall is a turn-based tactical football (soccer) game built on a hexagonal grid. It started as a personal project to explore what a chess-like football game would feel like — where positioning, resource management, and reading the opponent matter more than reflexes.

The engine is written in Python. Two teams of 11 players alternate turns, spending Action Points on moves and actions. Every contested moment — a tackle, a pass under pressure, a shot on goal — resolves with 3d6 dice rolls modified by player stats, keeping outcomes probabilistic but skill-weighted.

---

## How it Plays

**Turns & Action Points**
Each team takes a turn. Players have AP they can spend on actions. Spend wisely — overcommitting leaves you exposed.

**Actions**
- **Move** — reposition along the hex grid
- **Pass / Long Pass** — move the ball; contested by defenders in range
- **Shoot** — attempt a goal; GK dice roll determines the outcome
- **Tackle** — contest ball possession; both attacker and defender roll
- **Abilities** — special player-specific moves (slide tackle, through ball, power shot, sweeper punch, press trigger)

**Reactions**
Defending players can pre-declare a reaction before the attacking turn resolves. A goalkeeper can commit to a dive direction; a defender can declare an intercept lane or jockey stance. These add a bluffing / anticipation layer on top of the core dice system.

**Dice Model**
3d6 + stat bonus vs difficulty. The bell curve means truly elite players are reliably better, but underdogs can still win. Monte Carlo validation targets: equal teams → ~50% win rate each; elite striker vs average GK → ~30% goal rate; upset wins → 5–15%.

---

## Current State

**Sprint 5.7 complete** (as of mid-2026):

- Full 11v11 match engine
- All base actions + 5 special abilities
- Reaction system (GK Dive, Intercept Lane, Jockey, Press Trigger, First-Time Shot)
- Offside detection
- Auto-movement with tactical anchors and positional roles
- Heuristic AI with influence maps and multi-step planning
- Pygame watch-mode renderer + interactive human play
- Headless N-match batch simulator
- JSONL match logging + analytics dashboard
- 244 passing tests

---

## Tech Stack

| | |
|---|---|
| Language | Python 3.13 |
| Rendering | pygame |
| Config | YAML (config-driven, no hardcoded balance values) |
| State | Immutable frozen dataclasses (`MatchState`) |
| Testing | pytest (244 tests) |
| Simulation | Headless runner, JSONL logs, matplotlib dashboards |

---

## Why Hex?

Square grids feel unnatural for football — diagonal movement is weird and the geometry doesn't match how players actually spread across a pitch. Hex grids give 6 equidistant neighbours in every direction, which maps cleanly to football positioning: wide, central, forward, back. It also makes the line-of-sight maths for passes and shots much cleaner.
