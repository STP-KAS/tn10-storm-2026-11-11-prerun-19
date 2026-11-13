> **Experimental. We are just trying this.** [Disclaimer](../DISCLAIMER.md) · This page does not start a machine. Pre-run 19. Not Wednesday. Not Tuesday. Not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, or 18.

# Targets

There is no T0. There is no public clock. There is no latest minute. Nothing in pre-run 19 is scored: every step is an observation of whole minutes.

The hash file comes first and does not wait for the open. Nothing else in this page starts until the gates are true: Mini's TN10 node is synced with DAA moving; the desk's private TN10 node is up from its own data (PowerShell 7, no wipe) and synced; no Tuesday, Wednesday, or pre-run 1 to 18 runner is up; the operator has armed (no paste; see the README); our heavy lane's calibration on the node passed; and this repo's `logs/PRE-RUN-OPEN.md` is on origin.

## Order

1. **Nodes live.** Both TN10 nodes synced, DAA moving. No wipe.
2. **Calibration.** One lane transaction, read back from the desk mempool: node storage mass within 1 percent of our SDK's, fee rate 99–101. Otherwise the lane does not run and that is recorded.
3. **Hashes first.** [hashes/SIXTEEN.md](../hashes/README.md): sixteen rows, family label, tier, sha256 of the lowercase hex covenant id, and an On origin line.
4. **Families.** The sixteen covenant families start on the desk's private node, 1.2 hop/s offered. No payment sender of ours is started.
5. **Our one heavy lane** starts at N = 0 and follows one timeline of whole minutes set by the runner (lane 2 stays at N = 0 throughout):

| Order | File | The lane | Length |
|---:|---|---|---|
| 1 | BASE | 0 (control) | 3 whole minutes |
| 2 | HOLD-1 (the reference) | 30 at 150 | 4 whole minutes |
| 3 | HOLD-2 (greedy alone, part 1) | 30, greedy: wants 110 percent of its reference, never steps down | 6 whole minutes |
| 4 | HOLD-3 (greedy alone, part 2, no reset) | the same | 6 whole minutes |
| 5 | drain, HOLD-4 | 0 | the pinned minute; the bot sends only on a free third public kaspad, or files `NO SEND` |
| 6 | RETURN (after-run control) | 0 | 3 whole minutes |
| 7 | tail | families and lane stopped, the counter reads on | 5 minutes |

The lane's N changes on the minute boundary, on a timeline fixed when the lane starts. The minutes between HOLD-3's end and the pinned minute are the start of the drain; they are in `counts/chain/TIMELINE.md`. **Why such short steps:** the run is sized on the coins we hold after pre-run 18 (key 0 about 760 usable tKAS a family minute, 8,000 over the 18,000 line at the end; the sink is not swept): about 32 family minutes in all, of which the 12 greedy minutes are kept in one piece.

## Cohorts (families, node rates): the bystanders

| Cohort | Families | Rate, sompi/gram of node mass | Weight against the outside stream at 100, (rate/100)^3 |
|---|---|---:|---:|
| floor | 1–4 | 100, fixed | 1.00 |
| r150 | 5–8 | 150, fixed | 3.38 |
| r300 | 9–12 | 300, fixed | 27.0 |
| r450 | 13–16 | 450, fixed | 91.1 |

A hop is about 41,100–41,700 node mass (storage mass; compute 9,123), a lane transaction about 266,700. kit24 is pre-run 17's, unchanged; no family reads a live rate in this run.

## The greedy rule

Once a minute, at 22 seconds past the minute or later (the counter's line for the minute just closed is final about 20 seconds after it ends), the desk runner reads that minute and moves the lane's rate:

| What it is | Metric | Reference |
|---|---|---|
| the lane, 30 chains | lane transactions landed in the minute | the lane's median in HOLD-1 minutes 2–4 (at 150) |

- **greedy:** metric under 110 percent of the reference: rate × 1.25, rounded, at most 2,000; it never steps down; otherwise unchanged;
- an unread, partial or lagging minute holds the rate;
- **cap guard:** 4 decided minutes in a row at 2,000 → `CAP_REACHED` (minutes since the start, fees so far), back to 150, counters cleared;
- greedy alone starts at 150; its second part continues from where the first ended (no reset).

The new rate takes effect about 22 seconds into the next minute. The per-minute snapshot of the rate and every decision are in `logs/duel.log` (lane 2 shows 150 and never moves; it is off).

## Prediction, written before the run

- **Pre-run 18 says** a greedy lane against an equal normal-rule lane leapfrogs (150 → 1,405 in 21 minutes), with the pair's landings flat.
- **Our offline run of this controller** (`tools/sim/world19.mjs` with the runner's own controller code, `tools/sim/duelblock19.js`): a block-level toy world (10 blocks a second, 500,000 mass each, one heavy per block; a lane chain is ready again 4.2 s after its parent is included, a family chain 1.15 s; 3,100 other small transactions a minute; a draw that does not fit ends the block with probability 0.25; weighted by rate^3). Calibrated so that two lanes at 150 give the tiers about 52–56 / 78–82 / 97 / 100 percent of BASE and the two-lane greedy case leapfrogs as pre-run 18 did (to 1,756 in 24 minutes). **Alone, in every seed and for lane delays of 3.0 to 5.5 s, the lane is chain-limited:** it lands about 424 a minute at every rate, so it never reaches 110 percent of its reference and steps up every minute, 150 → 188 → … → 1,756 in 12 minutes. Toy fees 7,800–14,300 tKAS uncapped; our 4,500 cap would end it at about greedy minute 8–9 (rate about 719–899). In the toy the tiers are not hurt (one lane rarely holds more than one heavy ready).
- **What we expect in the real run:** a climb on its own, for the reason the toy gives: the lane at 150 already lands about what 30 chains can, so 110 percent is out of reach and the rule keeps stepping up. If the real lane does lose places to the r300 and r450 hops at 150, its landings will rise for a few steps and it may stop between 300 and 575. Our best guess: **about 60 percent that it climbs every minute until the fee cap (the budget ends it at about 700–900, a ceiling, not competition), about 40 percent that it settles between 300 and 575.**
- **How we tell them apart:** the lane's landings against its rate. Flat landings while the rate climbs = a ceiling (the greedy rule's own doing). Landings that rise with the rate and then hold over 110 percent = it was competing with the tiers.
- **Bystanders.** Less than pre-run 18 (one lane, half the heavy ready mass): floor and r150 below BASE at 150, and more as the lane climbs; r300 and r450 when the lane passes 300 and 450.
- **Other users** at up to about the lane's rate lose more the higher it goes.
- **Cost.** At 150 a lane transaction costs about 0.40 tKAS, at 600 about 1.6, at 2,000 about 5.34. The fee cap (4,500) may end the lane early; that is an answer too ("gave up (budget)").

## Our heavy lane

- **Shape.** One input (the chain's own coin, from the payment key), two plain pay-to-key outputs: 0.0375 tKAS to a dedicated sink key of ours, and the change back into the chain. Storage mass about 266,670 (KIP-9: 10^12 / 3,750,000 sompi for the small output, the change and input terms nearly cancel). Compute mass about 2,000. Fee rate × mass: about 0.40 tKAS at 150, 2.67 at 1,000 and 5.34 at the 2,000 cap.
- **Why this shape.** Our SDK counts every output at UTXO plurality 1 (pre-run 12's source check); plain outputs have plurality 1 on the node too, so the two agree. A covenant output (plurality 2) would be under-read by the SDK by a factor of four.
- **One lane, pre-run 18's process.** The lane uses chain slots 1–100 of pre-run 18's two-lane process (one node connection, one key-16 pile, its own N, rate and submit bucket: 1,200 a minute, 20 a second); lane 2 (slots 101–200) stays at N = 0 all run, so the counter's lane-2 column (hv2) should read 0.
- **Ready count.** A chain's next transaction goes out only after the previous one has left the desk mempool. So each lane has at most N entries in the mempool and all are ready. About one 267,000-mass transaction fits a 500,000 block, so at about 10 blocks a second the chain takes at most about 600 heavy transactions a minute, shared with any outside heavy. In pre-run 18, 30 + 30 chains held about 32–38 blocks of ready mass; 30 alone should hold about half that.
- **Money.** Only from the payment key (key 16: 796 coins, 13,623 tKAS, before this run's refill of key 0, which moved 430 of them, 7,923 tKAS; 366 coins, 5,700 tKAS, after). Each chain takes one pile coin and runs it down to under 2 tKAS, then takes the next. The family lane (key 0) is not touched by the heavy lane. The operator said tKAS is not a limit; the caps stay as guards, and the spend is logged.
- **Caps.** 1,200 lane submits a minute; pause above N + 2 lane entries for three probe samples; hold at mempool 90,000 or ready mass over 80 blocks; rate at most **2,000**; stop at **4,500** tKAS of fees or **4,700** tKAS moved, or the pile estimate under **1,000** tKAS (pre-run 18: 32,000 / 34,500 / 3,500); stop on any rejection that is not a timing one, or if the node's rate or mass on our own entries drifts from the calibration.
- **Not swept in this run.** The 0.0375 tKAS sink outputs (pre-runs 13 to 18's, about 130,000, and this run's) stay where they are, on the same sink key. A sweep is a separate, later, logged step.

## Why this shape

- Pre-run 18's greedy lane climbed against a rival. This run takes the rival away and keeps everything else (same lane, same rule, same tiers), so a climb here is the greedy rule against the tiers or against its own ceiling.
- HOLD-1 gives the lane its reference at the starting point (150); BASE gives the bystanders' reference.
- The steps are short because the run is sized on the coins we hold after pre-run 18 and the budget check before genesis must pass.
- No payments: the only load is the families, our lane and whatever other TN10 traffic is there.

## What we read

For each minute: the lane's N and rate and every decision (`logs/duel.log`); the lane landed (counter); hops per tier and each tier's node rate (as built and as the probe read it in the mempool) (desk counter, accepted on chain); our heavy in the mempool and ready (probe), our heavy landed (counter), lane submits (the lane's log); outside heavy at 100 (probe, entries not in our logs); the ready mass in blocks of 500,000 (from the full mempool read up to 10,000 entries, from the node's own figures above); the mempool size and the fee estimate. Mini is a second read of the hops.

## Selection rule

The desk node and the public kaspads answered serverVersion 2.1.0. In rusty-kaspa tag v2.1.0 (commit 01b532e8b553523216471682649693af92f0fd16), `mining/src/mempool/model/frontier.rs` takes every ready transaction best-first while the ready set's mass fits one block, and otherwise samples at random with weight (fee/mass)^3 (`ALPHA = 3`). Only a transaction with no parent in the mempool is ready, so a chained hop is not a candidate until its parent is out of the mempool. A higher fee raises the odds of being drawn; it does not buy a place in a queue. This is the source's rule, read from the code; the run reads the desk node's own template, not a miner's.

Abort line **18,000 usable tKAS** (key 0 coins over 3 tKAS, less 3 tKAS each). The coin count is logged, not a gate (pre-run 13 tripped on change fragments). Key 0 was consolidated and refilled before the open (sized on use; the runner's `BUDGET_CHECK`). Do not lower it.
