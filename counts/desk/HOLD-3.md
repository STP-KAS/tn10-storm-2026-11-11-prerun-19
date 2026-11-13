OBSERVATION

Not scored. No payment of ours in pre-run 19: families only, on the desk's private node, plus our own heavy lane at the N shown per minute.

# HOLD-3, desk, pre-run 19

> Our own TN10 testing: what we observed in this run, on our own desk node. Counts only. Included is what the desk's private TN10 node accepted on chain, read by the desk counter, by accepting chain block time. Mini's files are a second read.

HOLD-3 in pre-run 19 is greedy alone, part 2 (continued, no reset; no rival lane): L30-greedy-alone-2 6 whole minutes. Families only for payments (no payment of ours); our own heavy lane ran at the N and rate shown per minute (N = how many lane chains may each hold one ready transaction in the mempool). The HOLD file names are kept so the bot's and Mini's gates read as in earlier pre-runs. Not scored.

Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. No payment sender was started.

## Tiers against the mempool, per minute

| Minute (UTC) | Lane 1 N / rate | Lane 2 N / rate | floor (100) | r150 (150) | r300 (300) | r450 (450) | Our heavy in mempool / ready | Our heavy landed, lane 1 / lane 2 | Lane submits OK, lane 1 / lane 2 | Outside heavy at 100 (>200k mass) / ready | Outside at 100, n | Ready mass, blocks | Mempool | Fee estimate priority |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2026-11-13T05:24 | 30 / 460 | 0 / 150 | 17 | 39 | 127 | 167 | 27 / 27 | 521 / 0 | 522 / 0 | - / - | - | 25.17 | 295 | 667.0 |
| 2026-11-13T05:25 | 30 / 575 | 0 / 150 | 43 | 70 | 129 | 170 | 27 / 27 | 458 / 0 | 431 / 0 | - / - | - | 25.98 | 636 | 851.9 |
| 2026-11-13T05:26 | 30 / 719 | 0 / 150 | 186 | 189 | 192 | 187 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.50 | 17 | 162.4 |
| 2026-11-13T05:27 | 30 / 899 | 0 / 150 | 192 | 202 | 208 | 209 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 16 | 154.9 |
| 2026-11-13T05:28 | 30 / 1124 | 0 / 150 | 193 | 196 | 199 | 200 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 16 | 156.3 |
| 2026-11-13T05:29 | 30 / 1405 | 0 / 150 | 191 | 189 | 196 | 198 | 0 / 0 | 0 / 0 | 0 / 0 | - / - | - | 1.31 | 17 | 155.0 |

Lane 1 and lane 2 N / rate are the caps the runner set for that minute (N lane chains each, each chain with at most one ready transaction in the mempool) and each lane's fee rate (in the duel, the rate in effect at the start of the minute). Our heavy in mempool / ready is the probe's median count of our own lane entries; our heavy landed is what the desk counter read as accepted on chain from our lane in the minute; lane submits OK is the lane's own log. Hops are what the desk counter read as accepted on chain in that minute, per tier. Ready mass, blocks, is the median of the probe's samples in the minute (block limit 500,000). Outside at 100 is the median count of mempool entries not in our logs (our lane is in our logs) paying 100 sompi/gram, and heavy is how many of those had a mass over 200,000 (median of samples). The outside stream is not attributed to anyone.

## Chain, desk counter

| Minute (UTC) | Included, all non-coinbase | Our payments included | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Chain blocks | DAA gap max | Sink age max, ms | Final after, s | Counter |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T05:24 | 3,606 | 0 | 17 | 39 | 127 | 167 | 2,739 | 337 | 1 | 483 | 20 | kept pace |
| 2026-11-13T05:25 | 4,551 | 0 | 43 | 70 | 129 | 170 | 3,688 | 328 | 1 | 804 | 20 | kept pace |
| 2026-11-13T05:26 | 3,878 | 0 | 186 | 189 | 192 | 187 | 3,166 | 340 | 1 | 573 | 20 | kept pace |
| 2026-11-13T05:27 | 3,851 | 0 | 192 | 202 | 208 | 209 | 3,094 | 313 | 1 | 495 | 20 | kept pace |
| 2026-11-13T05:28 | 3,934 | 0 | 193 | 196 | 199 | 200 | 3,180 | 332 | 0 | 515 | 20 | kept pace |
| 2026-11-13T05:29 | 3,831 | 0 | 191 | 189 | 196 | 198 | 3,108 | 339 | 2 | 591 | 20 | kept pace |

Coinbase is taken out as one per merged blue block (on this node a chain block's accepted list carries the coinbase of each blue block it merges). Other traffic is the rest: other users' load, the genesis, and anything not in our logs.

## Hop rate per cohort, as built

Floor (families 1–4, desk private node): 100 sompi/gram per hop. R150 (families 5–8, desk private node): 150 sompi/gram per hop. R300 (families 9–12, desk private node): 300 sompi/gram per hop. R450 (families 13–16, desk private node): 450 sompi/gram per hop. In pre-run 19 that rate is on the hop's node-side mass (kit21): the builder is asked for a bill rate on its own mass so that fee / node mass is the tier's rate.

| Tier | Node rate as built, median (min–max) | Bill rate, median | Node mass, median (min–max) | Node rate in the desk mempool, lowest–highest (probe) |
|---|---|---:|---|---|
| floor (100) | 100.15 (100–100.32) | 313 | 40,752 (40,377–42,186) | 100.01–100.31 |
| r150 (150) | 150.17 (150–150.32) | 470 | 40,810 (40,384–42,219) | 150–150.31 |
| r300 (300) | 300.18 (300–300.32) | 939 | 40,791 (40,403–42,417) | 300–300.32 |
| r450 (450) | 450.16 (450–450.32) | 1408 | 40,804 (40,422–42,557) | 450–450.32 |

Node rate as built is kit21's fee / node mass (rusty-kaspa v2.1.0 storage mass with UTXO plurality, or compute or transient/2 if larger). In the desk mempool the probe divides the node's fee by the larger of the storage and compute mass the node reports.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 12 (384), 9 (377), 11 (362), 13 (356), 8 (349), 10 (342), 7 (321), 14 (295), 6 (282), 15 (260), 5 (250), 4 (231), and 15 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | R150 OK / att / rate rej / full rej / waiting | R300 OK / att / rate rej / full rej / waiting | R450 OK / att / rate rej / full rej / waiting | Family stalls logged | Family node mempool-high marks | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|---|---:|---:|---|
| 2026-11-13T05:24 | 0 | 0 | 0 | 0 | 0 | 17 / 291 / 0 / 0 / 4 | 39 / 300 / 0 / 0 / 4 | 127 / 346 / 0 / 0 / 4 | 167 / 359 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:25 | 0 | 0 | 0 | 0 | 0 | 43 / 306 / 0 / 0 / 4 | 70 / 320 / 0 / 0 / 4 | 129 / 351 / 0 / 0 / 4 | 170 / 372 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:26 | 0 | 0 | 0 | 0 | 0 | 186 / 363 / 0 / 0 / 4 | 189 / 362 / 0 / 0 / 4 | 192 / 361 / 0 / 0 / 4 | 187 / 358 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:27 | 0 | 0 | 0 | 0 | 0 | 192 / 360 / 0 / 0 / 4 | 202 / 376 / 0 / 0 / 4 | 208 / 375 / 0 / 0 / 4 | 209 / 377 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:28 | 0 | 0 | 0 | 0 | 0 | 193 / 370 / 0 / 0 / 4 | 196 / 371 / 0 / 0 / 4 | 199 / 376 / 0 / 0 / 4 | 200 / 376 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:29 | 0 | 0 | 0 | 0 | 0 | 191 / 366 / 0 / 0 / 4 | 189 / 367 / 0 / 0 / 4 | 196 / 383 / 0 / 0 / 4 | 198 / 386 / 0 / 0 / 4 | 0 | 0 | yes |

A family stall is a coordinator mark: no hop of that family landed for a while. The family was still attempting. It is logged, and it does not make the minute dirty.

A mempool-high mark means the family node read a mempool at or over 90,000. In pre-run 19 that does not stop the families: the skip does not apply to them. A skip, if one were set, is dirt with its reason (node-skip-fam) for every minute it covers, and it clears when the mempool falls back under the line.

Within 10 percent means 0 to 0 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 5. The family sender reads and submits every tier on the desk's private node, which the desk counter reads. The kept public kaspads are read for sync and DAA only; no payment of ours went to them.

Kept nodes are unique kaspads: each answered with its own node id at the preflight. 3 candidate endpoints passed the check and were 2 kaspads (node 4 is node 1; the second hostname was not used). 3 payment senders per kaspad.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 622118038 | 0 | 0 | 0 | 37 |
| 5 | yes | 622118038 | 0 | 0 | 0 | 37 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 822 of 822 | 1113 | 1766 |
| r150 | 885 of 885 | 1132 | 3147 |
| r300 | 1051 of 1051 | 1098 | 2319 |
| r450 | 1131 of 1131 | 1092 | 1714 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end. Every tier has the same hop shape and the same node; only the rate differs.

## Mempool and template, desk node (probe)

| Minute (UTC) | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T05:24 | 3 | 295 | 295 | 25.17 | 254 | 254 | - | - | 0 | 27 / 27 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 4 | 348,456 | 1 | 0 | 1 | 0 | 0 | 0 | 2 | 3 | 667.0 / 191.8 / 115.0 | 282 | 299 |
| 2026-11-13T05:25 | 3 | 636 | 644 | 25.98 | 603 | 603 | - | - | 0 | 27 / 27 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 3 | 267,602 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 2 | 851.9 / 194.2 / 115.2 | 626 | 639 |
| 2026-11-13T05:26 | 3 | 17 | 17 | 1.50 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,597 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 0 | 162.4 / 136.4 / 108.8 | 15 | 17 |
| 2026-11-13T05:27 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 489,896 | 0 | 0 | 0 | 2 | 3 | 4 | 4 | 0 | 154.9 / 133.0 / 108.2 | 1 | 1 |
| 2026-11-13T05:28 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,154 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 156.3 / 133.6 / 108.3 | 0 | 16 |
| 2026-11-13T05:29 | 3 | 17 | 17 | 1.31 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,173 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 0 | 155.0 / 133.0 / 108.2 | 14 | 17 |

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.
