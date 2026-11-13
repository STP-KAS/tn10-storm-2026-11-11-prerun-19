> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Counts only. No key, seed, txid, covenant id, address, host, or port.
>
> The desk counter's chain timeline for pre-run 19. Written by the desk runner after RETURN and a 5-minute tail.

# Chain timeline

Two files, `TIMELINE.md` and `MEMPOOL.md`, absent until the tail after RETURN is read.

Every minute the desk counter read on the desk's private TN10 node, by accepting chain block header time: all accepted non-coinbase transactions, our payments (none in pre-run 19), floor (100), r150, r300 and r450 family hops, our two lanes landed (hv1, hv2), other traffic, chain blocks, the desk node's DAA gap against a kept public kaspad, its sink age, and whether the counter kept pace. A minute marked `LAGGING`, `partial`, or `not final` is what the node had accepted then, not a network figure. Nothing is filled in. The tool is [tools/desk/counter.mjs](../../tools/desk/counter.mjs).

`MEMPOOL.md` (pre-run 19, lock line (xii)) is the probe's timeline: per minute, the median of the 20-second reads of the desk node's mempool (size, ready count, ready mass against one block, ours by cohort and payments, other traffic and its fee-rate buckets), the desk node's own block template by the same classes, the node's fee estimate, and the kept public kaspads' mempool sizes. Read-only; the template is never submitted. The minutes read before the open are in their own section. The tool is [tools/desk/mempool-probe.mjs](../../tools/desk/mempool-probe.mjs).
