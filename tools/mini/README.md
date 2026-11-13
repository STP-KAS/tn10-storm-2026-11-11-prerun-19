> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Kaspa Testnet-10 only. No id, key, address, host, or port in this folder.

# Mini's second read, pre-run 19

- `mini-runner.mjs`: pre-run 13's Mini counter, pointed at this repo (our heavy lane is other traffic to Mini), with pre-run 19's four fixed tiers (floor 1–4 100, r150 5–8, r300 9–12, r450 13–16; node rates) and the observation-only steps. One hop per transaction (lock line (xi)).
- `mini-classify-test.mjs`: offline check of the one-hop-per-transaction fix.
- `mini-dedupe-test.mjs`, `mini-dedupe.mjs`: pre-run 9's dedupe and its offline check, unchanged.
