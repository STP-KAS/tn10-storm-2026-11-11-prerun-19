> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Kaspa Testnet-10 only; tKAS has no value. Counts only.

> **Our own testing.** What this page shows is what our probe read on our own desk node in this run; it is not a claim of how TN10 behaves in general.

# Mempool and template timeline, pre-run 19

Read by the probe on the desk's private TN10 node every 20 s, read-only; each cell is the median of that minute's samples. Pre-run 17: ready count and ready mass come from the full mempool read up to 10,000 entries and from the node's own figures (getFeeEstimateExperimental, verbose) above that, where the per-class columns stay blank (the node's wRPC replies are capped at 128 MiB, about 12,500 entries). Ready means no parent in the mempool: in rusty-kaspa v2.1.0 only those are in the selector's frontier. Ready mass is compared with one block's mass limit (500,000): at or under 1 the selector takes all ready transactions best-first; over 1 it samples at random weighted by (fee/mass)^3 (over 4, sample_inplace). Mass is the larger of compute and storage mass, as the v2.1.0 selector normalises it (transient mass is not in the RPC). Other traffic is every mempool entry not in our sender logs (our heavy lane is its own class, our heavy); its fee rate is the node's fee over that mass. Template transactions carry no id in the RPC, so each is matched to a mempool entry by its first input. The template is the desk node's own getBlockTemplate (never submitted): what this node would put in a block at that moment, not a miner's template. The fee estimate is the node's getFeeEstimate, read only; no sender reads it. Public mempool is getInfo's mempool size on each kept public kaspad.

## The run

Step is the runner's step at the minute's start (see TIMELINE.md).

| Minute (UTC) | Step | Samples | Mempool | Ready (no parent in mempool) | Ready mass, blocks of 500k | Other traffic in mempool | Other ready | Other at 100, n | Other at 100, mean mass | Our payments in mempool | Our heavy in mempool / ready | Floor in mempool / ready | R150 in mempool / ready | R300 in mempool / ready | R450 in mempool / ready | Template txs | Template storage mass | Template txs over 100k storage mass | Template: payments | Template: our heavy | Template: floor | Template: r150 | Template: r300 | Template: r450 | Template: other | Fee estimate priority / normal / low | Public 1 mempool | Public 5 mempool |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|
| 2026-11-13T05:09 | BASE | 3 | 1 | 1 | 0.01 | 1 | 1 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 5,039 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 1 |
| 2026-11-13T05:10 | BASE | 2 | 17 | 17 | 1.31 | 1 | 1 | 1 | 4,477 | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 13 | 490,889 | 0 | 0 | 0 | 2 | 3 | 4 | 4 | 1 | 141.1 / 126.1 / 106.9 | 1 | 14 |
| 2026-11-13T05:11 | BASE | 3 | 16 | 17 | 1.32 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,921 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 138.8 / 124.8 / 106.6 | 1 | 13 |
| 2026-11-13T05:12 | BASE | 3 | 16 | 16 | 1.31 | 0 | 0 | 1 | 4,469 | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,917 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 139.2 / 125.0 / 106.7 | 50 | 65 |
| 2026-11-13T05:13 | BASE | 3 | 13 | 16 | 1.32 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 493,959 | 0 | 0 | 0 | 1 | 4 | 4 | 4 | 0 | 139.3 / 125.1 / 106.7 | 0 | 4 |
| 2026-11-13T05:14 | HOLD-1 | 3 | 61 | 65 | 17.77 | 23 | 23 | - | - | 0 | 26 / 26 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 9 | 367,929 | 1 | 0 | 1 | 1 | 0 | 1 | 4 | 2 | 259.5 / 165.4 / 112.7 | 45 | 59 |
| 2026-11-13T05:15 | HOLD-1 | 3 | 58 | 58 | 19.17 | 16 | 16 | - | - | 0 | 26 / 26 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 7 | 471,992 | 1 | 0 | 1 | 0 | 0 | 3 | 3 | 1 | 257.5 / 165.0 / 112.7 | 65 | 74 |
| 2026-11-13T05:16 | HOLD-1 | 3 | 62 | 70 | 19.98 | 30 | 30 | - | - | 0 | 25 / 25 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 470,209 | 1 | 0 | 1 | 0 | 1 | 2 | 3 | 1 | 264.2 / 166.3 / 112.8 | 44 | 56 |
| 2026-11-13T05:17 | HOLD-1 | 3 | 83 | 83 | 21.44 | 41 | 41 | - | - | 0 | 28 / 28 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 7 | 470,634 | 1 | 0 | 1 | 0 | 2 | 3 | 4 | 1 | 273.2 / 167.9 / 113.0 | 75 | 75 |
| 2026-11-13T05:18 | HOLD-2 | 3 | 77 | 86 | 21.57 | 42 | 42 | - | - | 0 | 27 / 27 | 4 / 4 | 3 / 3 | 4 / 4 | 3 / 3 | 8 | 471,714 | 1 | 0 | 1 | 0 | 1 | 1 | 3 | 2 | 266.9 / 166.8 / 112.9 | 61 | 66 |
| 2026-11-13T05:19 | HOLD-2 | 3 | 57 | 58 | 18.32 | 19 | 19 | - | - | 0 | 25 / 25 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 6 | 470,914 | 1 | 0 | 1 | 0 | 0 | 1 | 3 | 1 | 264.5 / 166.3 / 112.8 | 59 | 101 |
| 2026-11-13T05:20 | HOLD-2 | 3 | 86 | 86 | 18.08 | 49 | 49 | - | - | 0 | 23 / 23 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 8 | 470,568 | 1 | 0 | 1 | 0 | 0 | 2 | 2 | 2 | 307.9 / 173.1 / 113.5 | 79 | 75 |
| 2026-11-13T05:21 | HOLD-2 | 3 | 60 | 66 | 20.45 | 21 | 21 | - | - | 0 | 28 / 28 | 4 / 4 | 4 / 4 | 4 / 4 | 3 / 3 | 5 | 429,921 | 1 | 0 | 1 | 0 | 0 | 1 | 2 | 0 | 373.2 / 180.0 / 114.1 | 89 | 88 |
| 2026-11-13T05:22 | HOLD-2 | 3 | 144 | 155 | 19.27 | 113 | 113 | - | - | 0 | 23 / 23 | 4 / 4 | 4 / 4 | 3 / 3 | 3 / 3 | 6 | 349,391 | 1 | 0 | 1 | 0 | 0 | 0 | 1 | 3 | 429.2 / 184.0 / 114.4 | 188 | 194 |
| 2026-11-13T05:23 | HOLD-2 | 3 | 320 | 376 | 22.93 | 335 | 335 | - | - | 0 | 26 / 26 | 3 / 3 | 4 / 4 | 3 / 3 | 4 / 4 | 2 | 308,105 | 1 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 542.1 / 188.9 / 114.8 | 361 | 362 |
| 2026-11-13T05:24 | HOLD-3 | 3 | 295 | 295 | 25.17 | 254 | 254 | - | - | 0 | 27 / 27 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 4 | 348,456 | 1 | 0 | 1 | 0 | 0 | 0 | 2 | 3 | 667.0 / 191.8 / 115.0 | 282 | 299 |
| 2026-11-13T05:25 | HOLD-3 | 3 | 636 | 644 | 25.98 | 603 | 603 | - | - | 0 | 27 / 27 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 3 | 267,602 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 2 | 851.9 / 194.2 / 115.2 | 626 | 639 |
| 2026-11-13T05:26 | HOLD-3 | 3 | 17 | 17 | 1.50 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,597 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 0 | 162.4 / 136.4 / 108.8 | 15 | 17 |
| 2026-11-13T05:27 | HOLD-3 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 489,896 | 0 | 0 | 0 | 2 | 3 | 4 | 4 | 0 | 154.9 / 133.0 / 108.2 | 1 | 1 |
| 2026-11-13T05:28 | HOLD-3 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,154 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 156.3 / 133.6 / 108.3 | 0 | 16 |
| 2026-11-13T05:29 | HOLD-3 | 3 | 17 | 17 | 1.31 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,173 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 0 | 155.0 / 133.0 / 108.2 | 14 | 17 |
| 2026-11-13T05:30 | HOLD-4 | 3 | 6 | 6 | 0.58 | 0 | 0 | - | - | 0 | 0 / 0 | 3 / 3 | 2 / 2 | 0 / 0 | 0 / 0 | 6 | 291,252 | 0 | 0 | 0 | 1 | 2 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 2 |
| 2026-11-13T05:31 | HOLD-4 | 3 | 16 | 16 | 1.30 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 488,468 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 152.7 / 131.9 / 108.0 | 1 | 6 |
| 2026-11-13T05:32 | HOLD-4 | 3 | 9 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 449,685 | 0 | 0 | 0 | 1 | 2 | 4 | 4 | 0 | 153.1 / 132.1 / 108.0 | 50 | 57 |
| 2026-11-13T05:33 | HOLD-4 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 491,426 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 153.0 / 132.1 / 108.0 | 0 | 16 |
| 2026-11-13T05:34 | HOLD-4 | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,556 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 153.4 / 132.3 / 108.1 | 0 | 13 |
| 2026-11-13T05:35 | RETURN | 3 | 15 | 15 | 1.24 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 3 / 3 | 4 / 4 | 4 / 4 | 12 | 490,485 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 151.9 / 131.6 / 107.9 | 12 | 15 |
| 2026-11-13T05:36 | RETURN | 3 | 16 | 16 | 1.31 | 0 | 0 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,269 | 0 | 0 | 0 | 2 | 3 | 4 | 4 | 0 | 151.8 / 131.5 / 107.9 | 14 | 54 |
| 2026-11-13T05:37 | RETURN | 3 | 16 | 16 | 1.31 | 1 | 1 | - | - | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 489,064 | 0 | 0 | 0 | 2 | 2 | 4 | 4 | 1 | 151.5 / 131.4 / 107.9 | 0 | 9 |
| 2026-11-13T05:38 | RETURN | 3 | 17 | 17 | 1.31 | 1 | 1 | 1 | 2,518 | 0 | 0 / 0 | 4 / 4 | 4 / 4 | 4 / 4 | 4 / 4 | 12 | 490,755 | 0 | 0 | 0 | 1 | 3 | 4 | 4 | 0 | 150.9 / 131.1 / 107.8 | 1 | 17 |
| 2026-11-13T05:39 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | 1 | 13,368 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T05:40 | tail | 3 | 0 | 1 | 0.01 | 1 | 1 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T05:41 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T05:42 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 1 | 0 |
| 2026-11-13T05:43 | tail | 3 | 0 | 0 | 0.00 | 0 | 0 | 1 | 4,482 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 100.0 / 100.0 / 100.0 | 0 | 0 |
| 2026-11-13T05:44 | tail | 2 | 0 | 2 | 0.03 | 2 | 2 | - | - | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 174 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 2 | 100.0 / 100.0 / 100.0 | 0 | 2 |
