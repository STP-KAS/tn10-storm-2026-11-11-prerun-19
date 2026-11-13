> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> **This is the playbook for pre-run 19.** It is not Wednesday. It is not Tuesday. It is not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, or 18. It does not start a machine and it does not arm one.

# Playbook

Who does what, and the gates before each machine may start. The plan is [plan/PLAN.md](plan/PLAN.md), the locks are [locks/LOCKED.md](locks/LOCKED.md), and the go files are the three GO pages. This page does not override them.

## Oversight

TN10 ops oversees this rehearsal end to end: Mini, the desk (Build), and the bot. TN10 only. Never mainnet. Do not edit the Tuesday repo, the Wednesday repo, or pre-run 1's to 18's go files. Do not write `REVIEW_CLOSED`.

For pre-run 19 the operator does not paste. On 2026-11-12 he asked TN10 ops for covenant pre-runs under congestion and competition, pre-run 11 and then 12, 13 or more as needed (voice, 09:06 and 09:09 Brussels time), and at 10:04 in chat said "Keep exploring". That is the arm. The agents start their runners once the gates are facts.

## Start gates

1. **Mini node synced.** Existing TN10 kaspad, existing data, no wipe. `isSynced` true, DAA moving.
2. **Desk node synced.** Existing private TN10 kaspad, existing data, loopback only, started with `pwsh`. No wipe. Synced, DAA moving.
3. **No other runner.** No earlier runner, waiter, or counter on any machine. Lane above the abort line. The desk's private candidate list is present and not empty (`HELD candidates-missing` otherwise).
4. **Hashes.** `hashes/SIXTEEN.md` with sixteen rows and an On origin line, from [tools/sixteen](tools/sixteen/README.md).
5. **Open.** The desk pushes `logs/PRE-RUN-OPEN.md`. Mini then pushes `logs/MINI-ARMED.md`.
6. **Counter, families, senders.** The desk runner starts the counter on its private node and waits for its start line (`HELD counter-down` otherwise). Then the genesis from the bundle that wrote `hashes/SIXTEEN.md`, the families, and the payment steps.

## Who does what

| Who | Role | What not to do |
|---|---|---|
| **Desk (Build)** | Sends the sixteen families (four fixed tiers, one path, one build, kit24) and runs our own heavy lane in one lane process (one lane this time; the operator's OK, calibrated first). No payments. Its private TN10 node counts what the chain accepted (lock line (iv)) and its probe reads the mempool (xii). Publishes `hashes/SIXTEEN.md`, `logs/PRE-RUN-OPEN.md`, `counts/desk/` per step, `counts/chain/TIMELINE.md` and `MEMPOOL.md` after the tail, and `logs/METHOD.md`. | Do not stop or wipe the desk node. No Windows PowerShell 5.1, no `KaspaPublicNode`, no miner, no devnet. No 8- or 32-family publisher. No second runner. Never restart the runner mid-run. No payment sender. No heavy lane other than the runner's own lane process (which carries both lanes). |
| **Mini** | Second chain read on its own node. Does not send, mine, or hold a key. Publishes `logs/MINI-ARMED.md`, then `counts/mini/` when the matching desk file is on origin. | Do not wipe. Do not repeat the desk's head as Mini's. |
| **Bot (TN10 ops)** | Sends payments in the HOLD-4 minute only, on a synced public kaspad that is not one the desk kept, or publishes a legal `NO SEND`. | Do not send in any other step. One waiter. No local node. |

## Status when this repo was opened

Not a gate. Read on 2026-11-13 between 04:40Z and 04:45Z. This is our own TN10 testing; status lines are what we read on our own machines.

- Mini: existing TN10 kaspad 2.1.0 up, no wipe. Pre-run 18's Mini runner was in its 15-minute tail after RETURN and is left to end on its own; pre-run 19's Mini runner starts only after it has exited.
- Desk: existing private TN10 kaspad 2.1.0 up with `pwsh`, no wipe. It is not stopped for this pre-run. Pre-run 18's runner ended on its own at 04:23:43Z. `serve.mjs` and its keeper are not touched.
- Box: no local TN10 node. No bot waiter running.
- **Family lane** (key 0), read 04:40Z: 4,646 coins over 3 tKAS, **41,339 usable tKAS**, 1,451 small coins (3,444 tKAS). **Consolidated** 04:40:54Z: 20 transactions, none rejected, the 1,451 small coins into 127, 1.68 tKAS in fees. **Refilled from the payment pile** 04:40:55Z (`refill19.mjs`): 22 transactions, none rejected, 430 pile coins (7,923 tKAS) to key 0 at the same sizes, 0.99 tKAS in fees.
- **Sized on the funds we hold.** After pre-run 18 we hold about 41,000 usable tKAS on key 0 and 13,623 tKAS on the payment pile (796 coins); the sink outputs are not swept. The families use about 760 usable tKAS a minute, and the runner asks for 8,000 over the 18,000 line at the end. A run like pre-run 18's (about 60 family minutes) would need about 73,000 on key 0; we have about 57,600 in all. So this run is short: about **32 family minutes** (BASE 3, the reference 4, greedy alone 12, the drain to the pinned minute, RETURN 3, and the start), with no symmetric repeat. Read-only check `budget19.mjs`, 04:42Z: key 0 **50,838 usable**, less 760 a minute × 32 = **26,518 projected at the end**, over the 18,000 line by more than the 8,000 margin: ok. The runner repeats this check before genesis and holds the run if it fails.
- **The lane's budget is small.** The pile after the refill: **366 coins, 5,700 tKAS**. The lane's fee cap is **4,500 tKAS**, moved cap 4,700, pile floor 1,000. If the greedy lane climbs every minute, the fee cap can end it before the 12 greedy minutes are over; that is recorded as "gave up (budget)".
- Keys 1–15 got a fresh genesis coin from the family lane (15 transactions at 04:41:18Z, none rejected). After: key 0 5,188 coins over 3 tKAS, 50,838 usable, no small coins. Amounts and ids are in private notes.
- **Hop calibration on the node** (kit24, unchanged since pre-run 17), 04:42:07Z: one calibration covenant on key 0 (launch path `…-p19-cal`, not one of the sixteen families and not in `SIXTEEN.md`), its genesis, then two hops built by the family path and submitted on the desk's private node, each read back from the desk mempool:

| Hop | Builder bill rate (on 13,046) | kit24 storage mass | Node storage mass | Node compute mass | Fee, sompi | Node rate (fee ÷ node mass) |
|---|---:|---:|---:|---:|---:|---:|
| family 1 at 100 | 317 | 41,320 | 41,320 | 9,123 | 4,135,582 | 100.09 |
| family 13 (r450) at 450 | 1,436 | 41,603 | 41,603 | 9,123 | 18,734,056 | 450.31 |

  Storage mass matched to the unit and both node rates were within 1 percent of the asked rate (and not under it).
- **Our heavy lane's calibration:** at 2,000, 04:42:12Z: SDK storage mass 266,855, node 266,855 (0.00 percent off), compute 2,036, node rate 2,000.00 (fee 5.34 tKAS). At 100, 04:42:54Z: 266,673 on both sides, node rate 100.00. The sink key is pre-runs 13–18's (its parked outputs are not swept).
- The re-read just before `PRE-RUN-OPEN` (Mini's pre-run 18 runner ended, nodes synced, the bot's free check) is recorded in the offline rehearsal section below.
- Known risks, not fixed mid-run:
  - Our lane slows other TN10 users' transactions at fees up to about its own rate while it runs. If the greedy lane climbs, more of them wait. The operator OK'd our lane; the rate is capped at 2,000, the lane's fees at 4,500 tKAS, the cap guard puts it back to 150 after 4 minutes at the cap, and the lane steps down to zero at the end.
  - If the lane reaches its fee cap or the pile floor it stops for the rest of the run; that is recorded as "gave up (budget)", and the families go on.
  - A lone greedy lane can climb for a reason that is not competition: if 30 chains cannot land 110 percent of their reference at any rate (a ceiling). Its landings against its rate tell the two apart: if the rate rises and the landings do not, it is a ceiling.
  - Short segments: BASE 3 minutes and a 4-minute reference (median of minutes 2–4) are noisier than pre-run 18's 10.
  - The outside heavy fee-100 stream may also be there.
  - The rule reacts to the minute just closed and takes effect about 22 seconds into the next one.
  - The probe reads the desk node's mempool and template, not a miner's.
  - Only two unique public kaspads answered in every check so far, and the desk keeps both, so the bot is expected to file `NO SEND no-free-node`.

## Offline rehearsal, recorded before `PRE-RUN-OPEN`

Rehearsal `p19-a` ran on the desk against the fake node (no network for the sends), 2026-11-13 04:48:00Z to 05:06:59Z, with 2-minute lane steps (`STORM_LANE_MIN=2`, `STORM_RET_MIN=2`) and the probe's full read capped at 5,000 entries, using this pre-run's runner, lane, counter, probe, kit24 and family-fee files (the same files, by hash, as the live run).

- Preflight passed; `BUDGET_CHECK` logged (key 0 50,825 usable, 20 planned family minutes in the rehearsal, projected end 35,625, over the line plus margin); genesis 16 of 16 live; `FEE_SPLIT` verified floor 100, r150 150, r300 300, r450 450; `LANE_PLAN` BASE N0, HOLD-1 the reference (one lane), HOLD-2 greedy-alone-1, HOLD-3 greedy-alone-2, then the drain.
- One lane submitted with no rejections and no losses (4,140 OK); lane 2 stayed at N = 0 (0 submitted, the counter's lane-2 column 0).
- The SOLO controller did what the plan says: the reference from HOLD-1 for lane 1 only (lane 2's 0 did not hold it); in the greedy part the lane stepped up every minute (150 → 188 → 235 → 294; the fake node lands about the same at every rate, 96–103 percent of the reference, under 110 percent), **the second part continued from 188 without a reset**, and lane 2's rate never moved. No `ERROR` line; no cap in 2-minute steps.
- Every step file, TIMELINE, MEMPOOL and METHOD published to the rehearsal's local origin; `RUNNER_EXIT 0`.
- The cap guard and the budget hold were not reached in the rehearsal; the cap guard ran in the offline toy (`tools/sim/world19.mjs` with a 22-minute greedy part: `CAP_REACHED side=a` after 4 minutes at 2,000, back to 150, climbing again).

## Status after the live run

AFTER_PLACEHOLDER

### Public statement

We run our own heavy lane on TN10 in this pre-run, with the operator's OK, 30 chains: 4 minutes at 150, then 12 minutes at rates our greedy rule sets between 150 and 2,000 sompi/gram. While it runs, other TN10 users' transactions paying up to about the lane's rate wait longer on the nodes that see them, and more of them wait if the lane climbs. The figures for this run are added here after it. This is our own testing; tKAS has no value.

## When something breaks

Append a worked fix to [locks/LOCKED.md](locks/LOCKED.md) in the form that page shows, and a repair line to `logs/FIXES.md`. If the run dies before RETURN, write `logs/FAILED.md`, stop every runner, waiter, and counter, and do not resume. The next attempt is a new repo that starts from this repo's lock file.
