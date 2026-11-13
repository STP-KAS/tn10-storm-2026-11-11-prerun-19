> **Experimental. We are just trying this.** [Disclaimer](DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value.
>
> **This is a pre-run. Pre-run 19.** It is not the Wednesday run. It is not the Tuesday run. It is not pre-run 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, or 18. A read does not start a runner.

# tn10-storm-2026-11-11-prerun-19

**Pre-run 19 of the Wednesday neuron.** The neuron stays [tn10-storm-2026-11-11](https://github.com/STP-KAS/tn10-storm-2026-11-11). This repo does not edit that repo, does not write `REVIEW_CLOSED`, and does not set or move a clock for it. [tn10-storm-2026-11-10](https://github.com/STP-KAS/tn10-storm-2026-11-10) (Tuesday) is not edited from here either.

> **Our own testing.** This is our own Kaspa Testnet-10 testing, run on our own machines and nodes. What these pages report is what we observed in this run; it is not a claim of how TN10 or Kaspa behave in general.

**Where this starts.** Pre-runs 1 to 4 failed and are closed. Pre-runs 5 to 12 finished through RETURN and are closed. Pre-run 13 ran through the pinned HOLD-4 minute and failed in RETURN on its coin-count abort line; it is closed. Pre-runs 14, 15 and 16 finished through RETURN and are closed. Pre-run 17 failed before RETURN on its own abort line and is closed. Pre-run 18 finished through RETURN and is closed. The index of all of them is the [pre-run 2 README](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-2#pre-runs-in-this-rehearsal); the cumulative findings are in [tn-master](https://github.com/STP-KAS/tn-master). This repo starts from [pre-run 18's locks/LOCKED.md](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-18/blob/97c7460/locks/LOCKED.md) at commit 97c7460, copied here as [locks/LOCKED.md](locks/LOCKED.md), with a pre-run 19 section added at the end.

## What pre-run 18 left open

[Pre-run 18](https://github.com/STP-KAS/tn10-storm-2026-11-11-prerun-18) put a greedy heavy lane of ours (it wants 110 percent of its own reference and never steps down) against an equal lane on the normal rule. As we observed it, the pair leapfrogged from 150 to 1,405 and 1,124 in about 21 minutes while the two lanes together landed about the same each minute, so we read it as competition between the two, not capacity. What it could not say: **does a greedy lane climb on its own**, with no rival lane, only against the four fixed tiers? If it does, the climb in pre-run 18 was at least partly the greedy rule meeting a ceiling, not the rival.

## What pre-run 19 tries: greedy alone (the control)

The question: **does one greedy heavy lane (target 110 percent of its own reference, never steps down, cap 2,000) climb on its own against only the four fixed-rate family tiers, with no rival lane? If it climbs, do its landings rise with its rate (it was competing with the tiers) or stay flat (a ceiling of 30 chains)?**

> **We run our own heavy lane on TN10 again, and it slows other TN10 users' transactions.** In this pre-run we submit one bounded stream of our own heavy transactions (about 266,700 storage mass each, 30 chains, at rates our greedy rule sets between 150 and 2,000 sompi/gram) from our own test coins. While it runs, other TN10 users' transactions paying up to about the lane's rate wait longer; if the lane climbs, more of them wait. The operator gave the explicit OK for our lane (2026-11-12), said tKAS is not a limit and asked us to test at will. The lane is calibrated on the node first (at 100 and at 2,000), capped by ready count, by a per-minute submit cap, by a rate cap, by a cap guard and by a spend cap, stepped down to zero at the end, and every step is in this repo. This is our own testing; tKAS has no value.

- **One lane.** 30 chains in the lane process on the desk (pre-run 18's, with lane 2 at N = 0), each transaction about 266,700 storage mass, from the key-16 pile. About one such transaction fits a 500,000 block.
- **The greedy rule, once a minute:** if the lane landed under **110 percent** of its own reference, its rate goes up × 1.25 (cap **2,000**); it never steps down. It starts at 150. The reference is the lane's own median in HOLD-1 (minutes 2–4, at 150). A minute that is unread, partial or lagging holds. Every decision is logged (`logs/duel.log`, published after the run).
- **12 greedy minutes in one piece** (HOLD-2 and HOLD-3, 6 + 6, no reset). No symmetric repeat this time (no budget for it; pre-runs 17 and 18 saw that case).
- **Cap guard.** If the lane sits at 2,000 for 4 decided minutes in a row, the runner records it (`CAP_REACHED`) and puts it back to 150.
- **Bystanders.** The sixteen covenant families run at four fixed rates, node rates: floor (1–4) **100**, r150 (5–8) **150**, r300 (9–12) **300**, r450 (13–16) **450**. None of them moves.
- **Sized on the funds we hold.** We did not sweep the sink or add coins from outside. Key 0 (the families' coins) was consolidated and topped up from the pile to 50,838 usable tKAS; the runner checks before genesis that the usable tKAS projected at the end (760 a planned family minute) stays at least 8,000 over the 18,000 line, or it holds the run. That is why the segments are short. See [PLAYBOOK.md](PLAYBOOK.md#status-when-this-repo-was-opened).
- **Calibrated on the node before the open.** One hop at 100 and one at 450, and one lane transaction at 2,000 and one at 100, read back from the desk mempool.
- **Steps on one timeline:** BASE (the lane N = 0, 3 minutes), HOLD-1 (one lane, N = 30 at 150, no escalation: the reference, 4 minutes), HOLD-2 and HOLD-3 (greedy alone: the lane N = 30, 12 minutes in one piece, 6 + 6; it steps up whenever it landed under 110 percent of its reference and never steps down; no rival lane, only the four fixed tiers), then the lane N = 0 (the drain and the after-run control) through the pinned HOLD-4 minute and RETURN (3 minutes), then the counter's 5-minute tail. All are `OBSERVATION`. The HOLD file names are kept so the bot's and Mini's gates read as before.
- **Guards.** The lane keeps pre-run 18's guards (pause at N + 2 entries, hold at mempool 90,000 or ready mass over 80 blocks, stop on a non-timing rejection or a drift from the calibration, 1,200 submits a minute) with the fee cap at **4,500 tKAS**, the moved cap at 4,700 and the pile floor at 1,000 (pre-run 18: 32,000 / 34,500 / 3,500). If the lane meets a cap it stops for the rest of the run, and that is recorded as "gave up (budget)". The family lane's abort line stays **18,000 usable tKAS**.
- **What this can and cannot say.** One lane of ours, on one node, with a fixed reference and a greedy rule we chose; short segments; the outside heavy fee-100 stream may be there too. It cannot say how other people's wallets, other rules or other nodes would behave.

The prediction, written before the run, is in [plan/PLAN.md](plan/PLAN.md#prediction-written-before-the-run).

All locked lines from earlier pre-runs stay, except where the pre-run 19 block in [locks/LOCKED.md](locks/LOCKED.md) says what changes and why.

## Machines

| Machine | Go file | First sentence |
|---|---|---|
| Desk | [GO-DESK.md](GO-DESK.md) | DESK. I send and count on pre-run 19. This is not Wednesday. |
| Mini | [GO-MINI.md](GO-MINI.md) | MINI. I count pre-run 19 as the second read. I do not send. This is not Wednesday. |
| Bot | [GO-BOT.md](GO-BOT.md) | GROKBOT. I send payments on the pre-run 19 HOLD-4 only. I do not count. This is not Wednesday. |

The operator does not paste. On 2026-11-12 he asked TN10 ops for covenant pre-runs under congestion and competition, pre-run 11 and then 12, 13 or more as needed (voice, 09:06 and 09:09 Brussels time), and at 10:04 in chat said "Keep exploring". For our own heavy lane he gave the explicit OK in chat at about 11:08 and 11:10 Brussels time ("Do whatever you think is needed", then "No need to keep it short. Tn is for testing. Test at will"), and at 15:19 he said tKAS is not a limit ("Use all the tkas you want"). At 23:26 Brussels time he asked "Can we solve the fee escalation open question?", and at 23:28 said "launch run until you’re happy … Use all the tkas you want", and at about 23:30 "Yes keep going. At will." His word at 23:28 ("launch run until you’re happy … Use all the tkas you want") still stands. That is the arm for pre-run 19, its one heavy lane and the greedy-alone control. The agents start the runners once the gates are facts. [GO.md](GO.md) is the map, [PLAYBOOK.md](PLAYBOOK.md) has the roles and gates, and [plan/PLAN.md](plan/PLAN.md) has the targets and the reasons.

## Gates, in order

No clock. Each gate is a fact read from a node or from origin.

1. Mini's TN10 node is up from its own data, synced, DAA moving.
2. The desk's private TN10 node is up from its own data (PowerShell 7), synced, DAA moving.
3. No other runner or waiter is up. The family lane is above its abort line (18,000 usable tKAS). The desk's private candidate list is present.
4. `hashes/SIXTEEN.md` is on origin: sixteen rows and an On origin line, from the sixteen-family path.
5. The desk pushes `logs/PRE-RUN-OPEN.md`; Mini pushes `logs/MINI-ARMED.md`.
6. The probe and the desk counter are up. Then the families, our heavy lane at N = 0, and the observation steps on the lane's timeline.

Before the open: the hop calibration (node rate within 1 percent of 100 and of 450) and the lane's calibration (at 2,000 and at 100) passed.

## What a decent result is

- `hashes/SIXTEEN.md` on origin before the first family submit.
- Every step file on origin, each with hops per minute for the four tiers (floor, r150, r300, r450), each tier's node rate, each lane's N and rate, our heavy lane and the outside heavy apart, and the probe's table for the same minutes.
- `counts/chain/TIMELINE.md` and `counts/chain/MEMPOOL.md` after the tail, and RETURN on origin.
- The greedy lane's rate path, minute by minute, its landings against its rate, and an answer to the question (climbed on its own, settled, or gave up on budget; competition with the tiers or a ceiling), or an honest "not answered" with the reason.
- A HOLD-4 desk file, a bot file or a legal `NO SEND`, and a Mini file.
- The spend and the leftovers (the parked sink outputs, not swept) stated in the write-up.
- No id, txid, key, address, host, or port in this repo.

A miss stays in this repo. A next attempt is a new repo and starts from this repo's lock file.

**Part of [tn-master](https://github.com/STP-KAS/tn-master).** The rule is [docs/NEURON.md](https://github.com/STP-KAS/tn-master/blob/main/docs/NEURON.md). This pre-run is its own row. It is not row 47.
