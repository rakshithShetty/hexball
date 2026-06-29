---
layout: post
title: "How random should random be?"
date: 2026-06-29
categories: devlog
permalink: /dice-design/
---

I made an early decision to have randomness and risk-taking core part of the gameplay. Ofcourse this is nothing new to DnD players, but my direct was Baldur's Gate 3, I love how every action in the game goes through a dice check, which is fully transparent to the player. You can see the odds, you can add boosts to try to swing it your way. 

HexBall uses dice to resolve contested actions — tackles, shots, passes under pressure. However a football game is not just one action in isolation, it is a series of actions (pass-pass-pass-x10-goal). The tuning of the dice, success thresholds for different actions is critical to make it work. Get it wrong one way and you've built a spreadsheet — the better team always wins, nothing interesting ever happens, and there's no point playing out the match. Get it wrong the other way and you've built a slot machine — results are chaos, player quality is meaningless, and tactics don't actually matter.


## The simulation

I ran Monte Carlo simulations across three models — d20 (flat distribution), 2d6, and 3d6 — and tuned until the outcomes felt right. The targets I was aiming for:

- **Reasonable win-rates** → Passes should be easier, shots harder.
- **Elite striker (stat 85+) vs average keeper (stat 55)** → scoring maybe 50–60% of close shots, dropping off sharply with distance
- **Upsets** → the weaker player should win 5–15% of the time. Enough to matter. Not enough to feel broken.

Here's what came out:

![Dice simulation results](../assets/images/dice_sim_results.png)

---

## What the charts show

A few things jumped out once I had the data.

**Distance kills your shot.** Even an elite striker (stat 95) against a weak keeper (stat 40) goes from ~85% at point-blank to basically nothing by hex distance 10. That's intentional — it forces you to actually build attacks and work the ball into dangerous positions rather than just launching shots from anywhere.

**Skill gaps are real but not cruel.** A 90-stat attacker vs a 30-stat defender wins 96% of duels. Sounds dominant — but a 70 vs 70 matchup lands at about 45% for the attacker (slight defender advantage built in). And even the 30-stat player beats the 90-stat one 1.9% of the time. That 1.9% is the magic — it means every duel matters, and sometimes your tidy centre-back gets nutmegged by a League One reject.

**3d6 won.** The bell curve is the reason. Flat d20 swings too wildly — upsets were too common and skill felt irrelevant. 2d6 was better but the distribution peaked too sharply. 3d6 gives you that satisfying middle ground: most of the time the better player wins, but the tails are fat enough that football happens.

---

Building with this dice model for now. Everything else in the engine has been built on top of it, but software is modular enought to retune this once the full game is functional.

Next post: the reaction system — where the game stops being dice-rolling and starts feeling like actual football tactics.
