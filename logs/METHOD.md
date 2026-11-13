# Method, pre-run 19

> This is our own Kaspa Testnet-10 testing. What follows is what we observed in this run, on our own nodes; it is not a claim of how TN10 or Kaspa behave in general.

> Counts only. Desk side. Submit-OK is the desk sender log; included is the desk counter's read of what the desk's private TN10 node accepted on chain. Mini's files are a second read.

Steps (our own heavy lane on one absolute timeline): BASE = N0-control 3 min; HOLD-1 = L30-r150-ref 4 min; HOLD-2 = L30-greedy-alone-1 6 min; HOLD-3 = L30-greedy-alone-2 6 min; then N0-drain through the HOLD-4 minute and RETURN 3 min, then a 5-minute counter tail.

Our heavy lane, from its own log: 6,092 transactions submitted OK of 6,092, 0 rejected, 0 chains lost to an orphan timeout, 4,481 tKAS of fees and 228 tKAS parked on our own sink key, 343 payment-pile coins taken, stop state cap.

Accepted hops per cohort, as the desk's coordinator read them: floor 4,407, r150 4,949, r300 5,628, r450 5,793.

Per step (all OBSERVATION, families plus our own heavy lane, no payment of ours):

- BASE: OBSERVATION, submit-OK 0 / 0 / 0; our payments included 0 / 0 / 0; hops included floor/r150/r300/r450 552/566/583/572; counter minutes not kept-pace 0 of 3.
- HOLD-1: OBSERVATION, submit-OK 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 512/654/761/783; counter minutes not kept-pace 0 of 4.
- HOLD-2: OBSERVATION, submit-OK 0 / 0 / 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 473/735/1080/1176; counter minutes not kept-pace 0 of 6.
- HOLD-3: OBSERVATION, submit-OK 0 / 0 / 0 / 0 / 0 / 0; our payments included 0 / 0 / 0 / 0 / 0 / 0; hops included floor/r150/r300/r450 822/885/1051/1131; counter minutes not kept-pace 0 of 6.
- HOLD-4: OBSERVATION, submit-OK 0; our payments included 0; hops included floor/r150/r300/r450 185/187/187/187; counter minutes not kept-pace 0 of 1.
- RETURN: OBSERVATION, submit-OK 0 / 0 / 0; our payments included 0 / 0 / 0; hops included floor/r150/r300/r450 589/607/614/607; counter minutes not kept-pace 0 of 3.

Decent on the desk side: every step file reached origin.

## Selection rule, read before the run

The desk node and the kept public kaspads answered serverVersion 2.1.0 at the preflight. In rusty-kaspa tag v2.1.0 (commit 01b532e8b553523216471682649693af92f0fd16), `mining/src/mempool/model/frontier.rs` `build_selector` takes every ready transaction best-first while the ready set's mass fits one block, and otherwise samples at random with weight (fee/mass)^3 (`ALPHA = 3` in `mining/src/mempool/model/frontier/selectors.rs`, weight in `mining/src/mempool/model/frontier/feerate_key.rs`): `sample_inplace` above four blocks' mass, `MutatingTreeSelector` between one and four. Only a transaction with no parent in the mempool is in the ready set (`mining/src/mempool/model/transactions_pool.rs`), so a chained hop is not a candidate until its parent is out of the mempool. Against an outside stream at 100, the weights are 1.00 (100), 3.38 (150), 27.0 (300) and 91.1 (450), per unit of mass. In the duel our two lanes move between 100 and 2,000 (logs/duel.log, published after the run). A higher fee raises the odds; it does not buy a place in a queue. This is the source's rule, read from the code; the run does not see a miner's template.

Hop rates per hop, one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. Payments 150. The funding coins were not one size, so the fee is not called the whole cause. Every tier was read and submitted on the desk's private TN10 node, which also ran the counter. No payment sender was started; 2 unique public kaspads were read for sync only.

## Misses

- none

## Fixes

- none

## On origin

- counts/desk/BASE.md: 2026-11-13T05:14:21Z
- counts/desk/HOLD-1.md: 2026-11-13T05:18:21Z
- counts/desk/HOLD-2.md: 2026-11-13T05:24:21Z
- counts/desk/HOLD-3.md: 2026-11-13T05:30:22Z
- counts/desk/HOLD-4.md: 2026-11-13T05:35:22Z
- counts/desk/RETURN.md: 2026-11-13T05:39:22Z
- counts/chain/TIMELINE.md: 2026-11-13T05:44:35Z
- counts/chain/MEMPOOL.md: 2026-11-13T05:44:37Z
