> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> Our own testing. What we observed in this run, on our own nodes. Not a claim about how TN10 or Kaspa behave in general. No key, seed, txid, covenant id, address, host or port.

# Lessons, pre-run 19

Written after the run, 2026-11-13, from the files on origin and the desk's own logs (read-only). Times are UTC unless marked Brussels.

## Short version

- **Pre-run 19 ran through RETURN.** Every step file is on origin for the desk and for Mini, then TIMELINE, MEMPOOL and METHOD; every whole minute kept pace and was clean; no repair, no restart. All 6,092 lane transactions landed (0 rejected, 0 lost) and every OK family hop landed (floor 4,411, r150 4,953, r300 5,632, r450 5,797).
- **A greedy lane alone climbed too.** With no rival lane, only the four fixed tiers, our one greedy lane (steps up × 1.25 whenever it landed under 110 percent of its own reference, never steps down) went 150 → 188 → 235 → 294 → 368 → 460 → 575 → 719, one step every minute, 7 steps in 7 decided minutes. It never reached its target once.
- **It was a ceiling, not competition.** Its reference at 150 was 513 landed a minute; 110 percent is 564. While the rate went up almost five-fold its landings stayed flat: 458–559 a minute (median 518), 89–109 percent of the reference. It always had 23–28 transactions ready in the mempool, and the node merged about 570–628 blocks a minute, with room for about one of our 266,700-mass transactions a block. At 150 it already took about 85 percent of the blocks; 564 would have needed about 94 percent of every block, so paying more could not get it there.
- **The budget ended it, as written before the run.** The lane hit its moved cap (4,700 tKAS) at 05:25:46Z, 24 s after stepping to 719, with 4,481.21 tKAS of fees, and stopped for the rest of the run ("gave up (budget)"). The controller kept writing its rule after that (899, 1,124, 1,405, 1,756): those rates were never paid, there was no lane.
- **The fixed tiers were squeezed even though the lane landed no more.** Per family, percent of BASE (floor 100 / r150 / r300 / r450): at the reference 71 / 85 / 93 / 98; at 368 (05:23) 15 / 34 / 72 / 94; at 460 (05:24) 9 / 20 / 63 / 83. Within a minute of the lane stopping, all four tiers were back at 93–106 percent. The desk node's own block template (read, never submitted) shrank from about 470,000 mass and 6–9 transactions at 150 to 268,000–350,000 mass and 2–4 transactions at 368–575: our transaction plus very little else.
- Our lane slowed other TN10 users' transactions while it ran, less than in pre-run 18 but more as it climbed (below).

## The question

Pre-run 18 put a greedy lane against an equal lane on the normal rule; the pair leapfrogged from 150 to 1,405. Pre-run 18 read the climb as competition between the two lanes. Pre-run 19 is the control: **does a greedy lane climb on its own, with no rival, and if it does, is it because it competes with the tiers (landings rise with the rate) or because it meets a ceiling (landings flat)?**

The same lane process and rule as pre-run 18's lane 1: 30 chains, about 266,700 storage mass a transaction, from the key-16 pile; lane 2 at N = 0 all run (its counter column read 0 every minute). Once a minute, reading only its own landings against its HOLD-1 reference (at 150, minutes 2–4: **513** landed a minute): under 110 percent → × 1.25 (cap 2,000); otherwise unchanged; never down. Cap guard: 4 decided minutes at 2,000 → `CAP_REACHED`, back to 150 (not reached). Lane caps: 4,500 tKAS fees, 4,700 moved, pile floor 1,000.

## What happened

- Before the open: key 0's 1,451 small coins consolidated (20 transactions, fees 1.68), key 0 topped up from the pile (430 coins, 7,923 tKAS moved between our own keys, fees 0.99; 50,838 usable after), keys 1–15 funded. A budget check before genesis projected the end at 26,505 usable against the 18,000 line (8,000 margin) and passed. The segments are short because of this sizing (32 planned family minutes). Hop calibration at 100 and 450 and lane calibration at 2,000 and 100 matched the node. Offline rehearsal p19-a exited 0. The bot's free check ran once, read-only, before arming.
- Live run: desk runner from 05:08:52Z. BASE 05:11–05:13 (lane 0), HOLD-1 05:14–05:17 (30 at 150: the reference), HOLD-2 = greedy alone part 1 05:18–05:23, HOLD-3 = part 2 05:24–05:29 (no reset), drain (lane 0) from 05:30:00Z, HOLD-4 pinned minute 05:34, RETURN 05:36–05:38, then a 5-minute counter tail. `LANE_CAP` 05:25:46Z; `RUN_STOP return-closed` 05:39:24Z; `RUN end` 05:44:42Z.
- The lane was off from 05:25:46Z, so HOLD-3's last four minutes (05:26–05:29) are in effect a second control with the lane at 0.
- The outside heavy fee-100 stream of pre-runs 14–16 was absent (1 entry in two minutes, 0 otherwise).

## The rate path

Rates are those in effect at the start of each minute (a decision lands about 22 s into the next minute). Decisions are in [duel.log](duel.log).

| Minute | Rate in effect | Landed | % of reference (513) | Decision |
|---|---:|---:|---:|---|
| 05:18 | 150 | 515 | 100 | 150 → 188 |
| 05:19 | 150 → 188 at :22 | 521 | 102 | 188 → 235 |
| 05:20 | 188 | 496 | 97 | 235 → 294 |
| 05:21 | 235 | 527 | 103 | 294 → 368 |
| 05:22 | 294 | 559 | 109 | 368 → 460 |
| 05:23 | 368 | 504 | 98 | 460 → 575 |
| 05:24 | 460 | 521 | 102 | 575 → 719 |
| 05:25 | 575, 719 from :22, stopped at :46 | 458 | 89 | (899, not paid) |

- 7 steps up, 0 down, one every decided minute. The closest it came to its target was 109 percent (05:22, at 294).
- The highest rate actually paid was 719, for about 24 s.

## Ceiling against competition

| Reading | Pre-run 18 (two lanes, one greedy) | Pre-run 19 (greedy alone) |
|---|---|---|
| Greedy lane's reference at 150 | 275 (lane 2 286; together 548) | 513 |
| Greedy lane landed while climbing | 83–151 percent of reference, by taking places from lane 2 | 89–109 percent, flat |
| Heavy places the node gave our lanes a minute | 543–595 (together) | 458–559 |
| Merged blocks a minute | 575–643 | 570–628 |
| Why it kept stepping up | each time lane 2 caught up again | 564 a minute was more than the blocks hold for one heavy each |

- What this changes in pre-run 18's reading: the node gives our heavy transactions about one place a block (roughly 500–600 a minute here), whether one lane or two ask. In pre-run 18 the greedy lane could pass 110 percent only by taking lane 2's places, and lane 2 then stepped up to take them back: that leapfrog was competition between our two lanes. Alone, a 110 percent target sat above the ceiling from the first minute, so the same rule climbed with no one to compete with. **A target above the room there is climbs on its own; a rival only decides whether it can ever be met.**
- This is the outcome we gave about 60 percent before the run ("climbs every minute until the fee cap … a ceiling, not competition"). The toy's reason was wrong in detail: it had the lane chain-limited at about 424 a minute with about one transaction ready; the real lane landed about 513 with 23–28 ready, so its limit was the blocks, not its chains.

## Landing and cost

| Part | Lane rate | Floor % BASE | R150 % BASE | R300 % BASE | R450 % BASE | Lane landed, median | Other traffic, median | Fee est. priority, median | Ready, blocks, median | Mempool, median |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| BASE (3 min) | 0 | 100 (98–105) | 100 (91–102) | 100 (87–102) | 100 (84–101) | — | 3,137 | 139 | 1.3 | 16 |
| HOLD-1 ref (4) | 150 | 71 (67–72) | 85 (82–87) | 93 (90–102) | 98 (95–100) | 504 | 2,995 | 262 | 20 | 62 |
| Greedy part 1 (6) | 150 → 368 | 39 (15–72) | 66 (34–87) | 93 (72–97) | 98 (94–101) | 518 | 2,968 (2,691–3,171) | 341 | 20 | 82 |
| Greedy part 2, lane on (2) | 460 → 719 | 16 (9–24) | 28 (20–36) | 63 (63–64) | 84 (83–85) | 490 | 3,214 (2,739–3,688) | 759 | 26 | 466 |
| Greedy part 2, lane stopped (4) | 0 | 105 (102–106) | 100 (98–105) | 98 (95–103) | 99 (93–104) | — | 3,137 | 156 | 1.3 | 16 |
| RETURN (3) | 0 | 109 (104–110) | 105 (103–107) | 100 (99–105) | 101 (100–101) | — | 3,102 | 152 | 1.3 | 16 |

BASE per family: floor 45.5, r150 48.2, r300 50.5, r450 50.2 hops a minute.

- **Who lost.** As in pre-run 18, each tier fell once the lane paid about its rate or more: floor and r150 at once, r300 from about 294–368, r450 from about 460. Unlike pre-run 18, the lane did not land more for it; the tiers lost places that the lane did not take.
- **Why the tiers lost places the lane did not take (our reading, not proved).** The desk node's template shrank as the lane's rate rose (minute medians): about 491,000 mass and 12 transactions in BASE, 470,000 and 6–9 with the lane at 150, 308,000 (2 transactions) at 368, 348,000 (4) at 460, 268,000 (3) at 575. In rusty-kaspa v2.1.0 the selector samples ready transactions with weight (fee/mass)^3 when the ready set is over a block. With 23–28 of our heavy transactions ready at several times every other rate, almost every draw after the first is another of ours, which does not fit, and the template seems to close early with room left. Our extra ready transactions cost space without landing. We read the template of our own node only, not miners' templates.
- **Every OK hop still landed in the end**, as before: chains slowed, they did not lose hops.
- **Cost per lane transaction** is the rate × about 266,700 mass: 0.40 tKAS at 150, 0.50 at 188, 0.63 at 235, 0.78 at 294, 0.98 at 368, 1.23 at 460, 1.53 at 575, 1.92 at 719.
- **What greed bought.** In its 7 minutes and 46 s of greed the lane landed 4,101 (518 a minute, about 1 percent over its reference pace) for about 3,676 tKAS (fees 805 at the start of the greedy part, 4,481 at the cap): about 0.90 tKAS a landed transaction, about 2.2 times the reference cost, for no more places.

## Theory against what we observed

| Written before the run ([plan/PLAN.md](../plan/PLAN.md#prediction-written-before-the-run)) | Observed |
|---|---|
| About 60 percent: climbs every minute until the fee cap ends it at about 700–900, a ceiling, not competition. | Yes: a step every minute, ended by the moved cap at 719. |
| About 40 percent: its landings rise for a few steps (it competes with r300 / r450) and it settles between 300 and 575. | No: landings flat, it never settled. |
| Toy: chain-limited at about 424 a minute, rarely more than one heavy ready. | Not as the toy had it: about 513 a minute with 23–28 ready; the limit was the block room. |
| Toy: tiers not hurt. Plan: floor and r150 below BASE at 150, more as the lane climbs. | The plan, not the toy: floor 71 percent at 150 and 9 percent at 460. |
| Cost about 0.40 tKAS at 150, 1.6 at 600; the 4,500 cap may end it early. | 0.40 at 150; the moved cap (4,700) ended it first, at 05:25:46Z (fees 4,481). |

## Our lane slowed other TN10 users

With the lane on (05:14–05:25, 12 minutes), other traffic landed on our desk node had a median of 2,995 a minute at 150 (about 5 percent under BASE's 3,137) and 2,968 in the first greedy part (about 5 percent under; single minutes down to 2,691 at 05:23, about 14 percent under). Over the 12 minutes other traffic landed 36,028 against about 37,644 at BASE's pace (about 4 percent fewer); the rest waited: other users' ready transactions in the desk mempool grew from 16–49 a sample-minute median (HOLD-1 and early greedy) to 603 at 05:25, the mempool to 754 entries and the node's priority fee estimate to 931 (05:25:45Z) against 139 in BASE. Much of it landed when our lane stopped (3,688 other in the 05:25 minute). Our own floor hops at 100, a stand-in for a low-fee user, ran at 9 percent of their BASE pace with the lane at 460. We did this on purpose, with the operator's OK, in bounded steps, and it is in this repo's [public statement](../PLAYBOOK.md#public-statement).

## Bot

The bot sent nothing. Its waiter saw desk HOLD-3 on origin at 05:30:27Z (5 s after it got there) and pinned 05:34Z; its free check (05:33:20–05:33:31Z, before the minute) found the desk's kept nodes 1 and 5 (2 distinct kaspads) and every other node that answered on the same kaspad as a kept node. It filed `NO SEND no-free-node` in [counts/bot/HOLD-4.md](../counts/bot/HOLD-4.md) after the minute closed (on origin 05:35:04Z, first try). Coins were not the reason. No waiter fetch stalls this time.

## Mini

Mini read every published minute in full (3 / 4 / 6 / 6 / 1 / 3) and matched the desk in **92 of 92** cohort cells, with 0 removals after a minute had closed. Its TN10 kaspad was not wiped or restarted.

## Spend

| Item | tKAS |
|---|---:|
| Our heavy lane, fees | 4,481.21; 228.45 parked on our sink key, not swept |
| of which the greedy minutes (05:18–05:25:46Z) | about 3,676 |
| Family hops, fees (floor / r150 / r300 / r450) | 2,242.76 (180.50 / 304.00 / 691.07 / 1,067.19), node mass about 40,860–40,900 a hop |
| Consolidation and top-up of key 0 before the open | 2.67 (1.68 + 0.99); the top-up moved 7,923 tKAS between our own keys |
| Calibrations and genesis funding | a handful of single transactions |
| Bot | 0 |
| **About** | **6,730 in fees, plus 228 parked** |

Family submit results other than OK were `already_spent` and `orphan` only (the builder's waiting retries); 0 rate or full rejects.

Keys after the run (read-only status): key 0 4,159 coins over 3 tKAS, **28,381 usable** (50,825 at the budget check; abort line 18,000; projected 26,505), 1,029 small coins; keys 1–15 have no genesis coin. Payment pile (coins large enough to deal): **23 coins, 254 tKAS**; the payment key holds 3,077 coins, 6,626 tKAS in all, 2,830 of them of 1–3 tKAS (chain ends, not dealt).

## What this seems to show

- A lane that wants more than the room there is climbs on its own. Here a 110 percent target was above what the blocks hold for one heavy transaction each, from the first minute, so the rule stepped up every minute and stopped only when the money did.
- Paying more bought the lane nothing (flat landings, 2.2 times the cost) and cost the low-fee tiers and other users a lot; on our node the template seems to have closed early with our transactions ready.
- With pre-run 18: two lanes on one ceiling leapfrog; one lane on the same ceiling climbs alone. Either way the climb said more about the rule than about demand.
- What this cannot say: one run, 7 minutes 46 s of greed, short steps sized on our coins, one lane of ours on a fixed reference, one node's view, no outside stream; the cap (2,000) and the cap guard were not reached. We are just testing.

## Every minute

Rates in effect at the start of the minute; decisions are the duel log's (rate before → after, applied about 22 s into the next minute). Merged blocks is the counter's coinbase count from the duel log (duel minutes only). Template is the desk node's own template (transactions / storage mass, median of the minute). Drain minutes 05:30–05:33 and 05:35 are not step minutes.

| Min (UTC) | Step | Part | Lane rate in effect | Floor / fam (% BASE) | R150 / fam | R300 / fam | R450 / fam | Lane landed | % of ref | Decision | Other traffic | Merged blocks | Ready, blocks | Mempool | Fee est. priority | Template n / mass |
|---|---|---|---|---:|---:|---:|---:|---:|---:|---|---:|---:|---:|---:|---:|---|
| 05:11 | BASE | BASE | 0 | 45.5 (100%) | 49.2 (102%) | 50.5 (100%) | 50.2 (100%) | 0 | — | — | 3,137 | — | 1.32 | 16 | 138.8 | 12 / 490,921 |
| 05:12 | BASE | BASE | 0 | 44.5 (98%) | 44.0 (91%) | 43.8 (87%) | 42.0 (84%) | 0 | — | — | 3,108 | — | 1.31 | 16 | 139.2 | 12 / 491,917 |
| 05:13 | BASE | BASE | 0 | 48.0 (105%) | 48.2 (100%) | 51.5 (102%) | 50.8 (101%) | 0 | — | — | 3,165 | — | 1.32 | 13 | 139.3 | 12 / 493,959 |
| 05:14 | HOLD-1 | ref | 150 | 30.5 (67%) | 39.8 (82%) | 46.5 (92%) | 49.0 (98%) | 462 | — | — | 2,986 | — | 17.77 | 61 | 259.5 | 9 / 367,929 |
| 05:15 | HOLD-1 | ref | 150 | 32.8 (72%) | 41.8 (87%) | 47.0 (93%) | 49.0 (98%) | 522 | — | — | 3,021 | — | 19.17 | 58 | 257.5 | 7 / 471,992 |
| 05:16 | HOLD-1 | ref | 150 | 32.8 (72%) | 40.0 (83%) | 45.2 (90%) | 47.8 (95%) | 494 | — | — | 3,004 | — | 19.98 | 62 | 264.2 | 7 / 470,209 |
| 05:17 | HOLD-1 | ref | 150 | 32.0 (70%) | 42.0 (87%) | 51.5 (102%) | 50.0 (100%) | 513 | — | — | 2,977 | — | 21.44 | 83 | 273.2 | 7 / 470,634 |
| 05:18 | HOLD-2 | greedy 1 | 150 | 32.8 (72%) | 41.8 (87%) | 48.5 (96%) | 49.0 (98%) | 515 | 100% | 150 → 188 | 3,020 | 604 | 21.57 | 77 | 266.9 | 8 / 471,714 |
| 05:19 | HOLD-2 | greedy 1 | 150 | 29.0 (64%) | 39.2 (81%) | 48.8 (97%) | 50.8 (101%) | 521 | 102% | 188 → 235 | 3,014 | 608 | 18.32 | 57 | 264.5 | 6 / 470,914 |
| 05:20 | HOLD-2 | greedy 1 | 188 | 18.2 (40%) | 35.8 (74%) | 48.0 (95%) | 50.0 (100%) | 496 | 97% | 235 → 294 | 3,171 | 579 | 18.08 | 86 | 307.9 | 8 / 470,568 |
| 05:21 | HOLD-2 | greedy 1 | 235 | 17.2 (38%) | 27.5 (57%) | 45.5 (90%) | 49.5 (99%) | 527 | 103% | 294 → 368 | 2,923 | 606 | 20.45 | 60 | 373.2 | 5 / 429,921 |
| 05:22 | HOLD-2 | greedy 1 | 294 | 14.2 (31%) | 23.2 (48%) | 43.0 (85%) | 47.8 (95%) | 559 | 109% | 368 → 460 | 2,794 | 628 | 19.27 | 144 | 429.2 | 6 / 349,391 |
| 05:23 | HOLD-2 | greedy 1 | 368 | 6.8 (15%) | 16.2 (34%) | 36.2 (72%) | 47.0 (94%) | 504 | 98% | 460 → 575 | 2,691 | 570 | 22.93 | 320 | 542.1 | 2 / 308,105 |
| 05:24 | HOLD-3 | greedy 2 | 460 | 4.2 (9%) | 9.8 (20%) | 31.8 (63%) | 41.8 (83%) | 521 | 102% | 575 → 719 | 2,739 | 605 | 25.17 | 295 | 667.0 | 4 / 348,456 |
| 05:25 | HOLD-3 | greedy 2 | 575 | 10.8 (24%) | 17.5 (36%) | 32.2 (64%) | 42.5 (85%) | 458 | 89% | 719 → 899 | 3,688 | 604 | 25.98 | 636 | 851.9 | 3 / 267,602 |
| 05:26 | HOLD-3 | greedy 2 | stopped (cap); controller 719 | 46.5 (102%) | 47.2 (98%) | 48.0 (95%) | 46.8 (93%) | 0 | — | 899 → 1124 (paper) | 3,166 | 496 | 1.5 | 17 | 162.4 | 12 / 490,597 |
| 05:27 | HOLD-3 | greedy 2 | stopped (cap); controller 899 | 48.0 (105%) | 50.5 (105%) | 52.0 (103%) | 52.2 (104%) | 0 | — | 1124 → 1405 (paper) | 3,094 | 498 | 1.31 | 16 | 154.9 | 12 / 489,896 |
| 05:28 | HOLD-3 | greedy 2 | stopped (cap); controller 1124 | 48.2 (106%) | 49.0 (102%) | 49.8 (99%) | 50.0 (100%) | 0 | — | 1405 → 1756 (paper) | 3,180 | 530 | 1.31 | 16 | 156.3 | 12 / 491,154 |
| 05:29 | HOLD-3 | greedy 2 | stopped (cap); controller 1405 | 47.8 (105%) | 47.2 (98%) | 49.0 (97%) | 49.5 (99%) | 0 | — | — | 3,108 | — | 1.31 | 17 | 155.0 | 12 / 490,173 |
| 05:34 | HOLD-4 | drain | 0 | 46.2 (102%) | 46.8 (97%) | 46.8 (93%) | 46.8 (93%) | 0 | — | — | 3,079 | — | 1.31 | 16 | 153.4 | 12 / 490,556 |
| 05:36 | RETURN | N = 0 | 0 | 50.2 (110%) | 51.8 (107%) | 53.2 (105%) | 51.0 (101%) | 0 | — | — | 3,140 | — | 1.31 | 16 | 151.8 | 12 / 490,269 |
| 05:37 | RETURN | N = 0 | 0 | 47.5 (104%) | 50.5 (105%) | 50.5 (100%) | 50.0 (100%) | 0 | — | — | 3,102 | — | 1.31 | 16 | 151.5 | 12 / 489,064 |
| 05:38 | RETURN | N = 0 | 0 | 49.5 (109%) | 49.5 (103%) | 49.8 (99%) | 50.8 (101%) | 0 | — | — | 3,081 | — | 1.31 | 17 | 150.9 | 12 / 490,755 |

## What a next attempt could try (not opened)

- **A greedy target under the ceiling:** the same lane alone with its target at 100–105 percent, to see whether it settles when the target can be met.
- **Fewer chains ready** (N = 5–10 instead of 30) at the same climb, to test our reading that our own extra ready transactions shrank the template; read the template every few seconds.
- **The cap run** (the greedy climb to 2,000 and the cap guard) needs a much larger lane budget (at 2,000 a lane transaction is about 5.3 tKAS, about 2,700 tKAS a minute for one lane) and so a pile refill first; the pile is down to 254 dealable tKAS, and the sink is not swept (a separate, later, logged step).
