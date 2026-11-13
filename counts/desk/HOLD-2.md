OBSERVATION

Not scored. No payment of ours in pre-run 19: families only, on the desk's private node, plus our own heavy lane at the N shown per minute.

# HOLD-2, desk, pre-run 19

> Our own TN10 testing: what we observed in this run, on our own desk node. Counts only. Included is what the desk's private TN10 node accepted on chain, read by the desk counter, by accepting chain block time. Mini's files are a second read.

HOLD-2 in pre-run 19 is greedy alone, part 1 (one lane, N=30 from 150, greedy: wants 110 percent of its reference and never steps down; no rival lane, only the four fixed tiers): L30-greedy-alone-1 6 whole minutes. Families only for payments (no payment of ours); our own heavy lane ran at the N and rate shown per minute (N = how many lane chains may each hold one ready transaction in the mempool). The HOLD file names are kept so the bot's and Mini's gates read as in earlier pre-runs. Not scored.

Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder: floor (families 1–4) 100 sompi/gram on the desk's private node, r150 (families 5–8) 150 sompi/gram on the desk's private node, r300 (families 9–12) 300 sompi/gram on the desk's private node, r450 (families 13–16) 450 sompi/gram on the desk's private node. No payment sender was started.

## Tiers against the mempool, per minute

| Minute (UTC) | Lane 1 N / rate | Lane 2 N / rate | floor (100) | r150 (150) | r300 (300) | r450 (450) | Our heavy in mempool / ready | Our heavy landed, lane 1 / lane 2 | Lane submits OK, lane 1 / lane 2 | Outside heavy at 100 (>200k mass) / ready | Outside at 100, n | Ready mass, blocks | Mempool | Fee estimate priority |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2026-11-13T05:18 | 30 / 150 | 0 / 150 | 131 | 167 | 194 | 196 | 27 / 27 | 515 / 0 | 507 / 0 | - / - | - | 21.57 | 77 | 266.9 |
| 2026-11-13T05:19 | 30 / 150 | 0 / 150 | 116 | 157 | 195 | 203 | 25 / 25 | 521 / 0 | 520 / 0 | - / - | - | 18.32 | 57 | 264.5 |
| 2026-11-13T05:20 | 30 / 188 | 0 / 150 | 73 | 143 | 192 | 200 | 23 / 23 | 496 / 0 | 504 / 0 | - / - | - | 18.08 | 86 | 307.9 |
| 2026-11-13T05:21 | 30 / 235 | 0 / 150 | 69 | 110 | 182 | 198 | 28 / 28 | 527 / 0 | 525 / 0 | - / - | - | 20.45 | 60 | 373.2 |
| 2026-11-13T05:22 | 30 / 294 | 0 / 150 | 57 | 93 | 172 | 191 | 23 / 23 | 559 / 0 | 548 / 0 | - / - | - | 19.27 | 144 | 429.2 |
| 2026-11-13T05:23 | 30 / 368 | 0 / 150 | 27 | 65 | 145 | 188 | 26 / 26 | 504 / 0 | 514 / 0 | - / - | - | 22.93 | 320 | 542.1 |

Lane 1 and lane 2 N / rate are the caps the runner set for that minute (N lane chains each, each chain with at most one ready transaction in the mempool) and each lane's fee rate (in the duel, the rate in effect at the start of the minute). Our heavy in mempool / ready is the probe's median count of our own lane entries; our heavy landed is what the desk counter read as accepted on chain from our lane in the minute; lane submits OK is the lane's own log. Hops are what the desk counter read as accepted on chain in that minute, per tier. Ready mass, blocks, is the median of the probe's samples in the minute (block limit 500,000). Outside at 100 is the median count of mempool entries not in our logs (our lane is in our logs) paying 100 sompi/gram, and heavy is how many of those had a mass over 200,000 (median of samples). The outside stream is not attributed to anyone.

## Chain, desk counter

| Minute (UTC) | Included, all non-coinbase | Our payments included | Floor hops (100) | R150 hops (150) | R300 hops (300) | R450 hops (450) | Other traffic | Chain blocks | DAA gap max | Sink age max, ms | Final after, s | Counter |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 2026-11-13T05:18 | 4,201 | 0 | 131 | 167 | 194 | 196 | 3,020 | 342 | 1 | 546 | 20 | kept pace |
| 2026-11-13T05:19 | 4,200 | 0 | 116 | 157 | 195 | 203 | 3,014 | 341 | 1 | 439 | 20 | kept pace |
| 2026-11-13T05:20 | 4,274 | 0 | 73 | 143 | 192 | 200 | 3,171 | 330 | 1 | 618 | 20 | kept pace |
| 2026-11-13T05:21 | 4,000 | 0 | 69 | 110 | 182 | 198 | 2,923 | 340 | 2 | 450 | 20 | kept pace |
| 2026-11-13T05:22 | 3,859 | 0 | 57 | 93 | 172 | 191 | 2,794 | 348 | 1 | 607 | 20 | kept pace |
| 2026-11-13T05:23 | 3,619 | 0 | 27 | 65 | 145 | 188 | 2,691 | 323 | 2 | 448 | 20 | kept pace |

Coinbase is taken out as one per merged blue block (on this node a chain block's accepted list carries the coinbase of each blue block it merges). Other traffic is the rest: other users' load, the genesis, and anything not in our logs.

## Hop rate per cohort, as built

Floor (families 1–4, desk private node): 100 sompi/gram per hop. R150 (families 5–8, desk private node): 150 sompi/gram per hop. R300 (families 9–12, desk private node): 300 sompi/gram per hop. R450 (families 13–16, desk private node): 450 sompi/gram per hop. In pre-run 19 that rate is on the hop's node-side mass (kit21): the builder is asked for a bill rate on its own mass so that fee / node mass is the tier's rate.

| Tier | Node rate as built, median (min–max) | Bill rate, median | Node mass, median (min–max) | Node rate in the desk mempool, lowest–highest (probe) |
|---|---|---:|---|---|
| floor (100) | 100.16 (100–100.32) | 313 | 40,812 (40,377–41,932) | 100–100.31 |
| r150 (150) | 150.17 (150–150.32) | 470 | 40,831 (40,383–42,100) | 150–150.32 |
| r300 (300) | 300.16 (300–300.32) | 940 | 40,839 (40,403–42,396) | 300.01–300.31 |
| r450 (450) | 450.16 (450–450.32) | 1410 | 40,856 (40,423–42,599) | 450.01–450.32 |

Node rate as built is kit21's fee / node mass (rusty-kaspa v2.1.0 storage mass with UTXO plurality, or compute or transient/2 if larger). In the desk mempool the probe divides the node's fee by the larger of the storage and compute mass the node reports.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 12 (411), 11 (381), 13 (376), 9 (354), 10 (352), 14 (333), 8 (324), 15 (300), 7 (290), 16 (265), 6 (260), 5 (227), and 16 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | R150 OK / att / rate rej / full rej / waiting | R300 OK / att / rate rej / full rej / waiting | R450 OK / att / rate rej / full rej / waiting | Family stalls logged | Family node mempool-high marks | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|---|---:|---:|---|
| 2026-11-13T05:18 | 0 | 0 | 0 | 0 | 0 | 131 / 338 / 0 / 0 / 4 | 167 / 357 / 0 / 0 / 4 | 194 / 370 / 0 / 0 / 4 | 196 / 371 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:19 | 0 | 0 | 0 | 0 | 0 | 116 / 335 / 0 / 0 / 4 | 157 / 347 / 0 / 0 / 4 | 195 / 374 / 0 / 0 / 4 | 203 / 376 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:20 | 0 | 0 | 0 | 0 | 0 | 73 / 314 / 0 / 0 / 4 | 143 / 352 / 0 / 0 / 4 | 191 / 371 / 0 / 0 / 3 | 196 / 377 / 0 / 0 / 0 | 0 | 0 | yes |
| 2026-11-13T05:21 | 0 | 0 | 0 | 0 | 0 | 69 / 309 / 0 / 0 / 4 | 109 / 337 / 0 / 0 / 3 | 183 / 367 / 0 / 0 / 4 | 202 / 383 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:22 | 0 | 0 | 0 | 0 | 0 | 57 / 310 / 0 / 0 / 4 | 94 / 330 / 0 / 0 / 4 | 172 / 353 / 0 / 0 / 4 | 191 / 373 / 0 / 0 / 4 | 0 | 0 | yes |
| 2026-11-13T05:23 | 0 | 0 | 0 | 0 | 0 | 27 / 297 / 0 / 0 / 4 | 65 / 314 / 0 / 0 / 4 | 145 / 351 / 0 / 0 / 4 | 188 / 369 / 0 / 0 / 4 | 0 | 0 | yes |

A family stall is a coordinator mark: no hop of that family landed for a while. The family was still attempting. It is logged, and it does not make the minute dirty.

A mempool-high mark means the family node read a mempool at or over 90,000. In pre-run 19 that does not stop the families: the skip does not apply to them. A skip, if one were set, is dirt with its reason (node-skip-fam) for every minute it covers, and it clears when the mempool falls back under the line.

Within 10 percent means 0 to 0 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 5. The family sender reads and submits every tier on the desk's private node, which the desk counter reads. The kept public kaspads are read for sync and DAA only; no payment of ours went to them.

Kept nodes are unique kaspads: each answered with its own node id at the preflight. 3 candidate endpoints passed the check and were 2 kaspads (node 4 is node 1; the second hostname was not used). 3 payment senders per kaspad.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 622114426 | 0 | 0 | 0 | 37 |
| 5 | yes | 622114426 | 0 | 0 | 0 | 37 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 473 of 473 | 2007 | 8483 |
| r150 | 735 of 735 | 1481 | 4217 |
| r300 | 1080 of 1080 | 1151 | 1844 |
| r450 | 1176 of 1176 | 1078 | 1543 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end. Every tier has the same hop shape and the same node; only the rate differs.

## Mempool and template, desk node (probe)

| Minute (UTC) | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T05:18 | 3 | 77 | 86 | 21.57 | 42 | 42 | - | - | 0 | 27 / 27 | 4 / 4 | 3 / 3 | 4 / 4 | 3 / 3 | 8 | 471,714 | 1 | 0 | 1 | 0 | 1 | 1 | 3 | 2 | 266.9 / 166.8 / 112.9 | 61 | 66 |
| 2026-11-13T05:19 | 3 | 57 | 58 | 18.32 | 19 | 19 | - | - | 0 | 25 / 25 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 470,914 | 1 | 0 | 1 | 0 | 0 | 1 | 3 | 1 | 264.5 / 166.3 / 112.8 | 59 | 101 |
| 2026-11-13T05:20 | 3 | 86 | 86 | 18.08 | 49 | 49 | - | - | 0 | 23 / 23 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 8 | 470,568 | 1 | 0 | 1 | 0 | 0 | 2 | 2 | 2 | 307.9 / 173.1 / 113.5 | 79 | 75 |
| 2026-11-13T05:21 | 3 | 60 | 66 | 20.45 | 21 | 21 | - | - | 0 | 28 / 28 | 4 / 4 | 4 / 4 | 4 / 4 | 3 / 3 | 5 | 429,921 | 1 | 0 | 1 | 0 | 0 | 1 | 2 | 0 | 373.2 / 180.0 / 114.1 | 89 | 88 |
| 2026-11-13T05:22 | 3 | 144 | 155 | 19.27 | 113 | 113 | - | - | 0 | 23 / 23 | 4 / 4 | 4 / 4 | 3 / 3 | 3 / 3 | 6 | 349,391 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 3 | 429.2 / 184.0 / 114.4 | 188 | 194 |
| 2026-11-13T05:23 | 3 | 320 | 376 | 22.93 | 335 | 335 | - | - | 0 | 26 / 26 | 3 / 3 | 4 / 4 | 3 / 3 | 4 / 4 | 2 | 308,105 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 542.1 / 188.9 / 114.8 | 361 | 362 |

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.
