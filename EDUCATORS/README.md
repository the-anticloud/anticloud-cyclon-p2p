# Educators — CYCLON_P2P

**Project:** CYCLON_P2P  
**Category:** SOCIAL_MEDIA  
**Upstream:** https://github.com/nicktindall/cyclon.p2p  
**Pinned commit:** `75866f03fd9bb7de0abde920bd4761660de5a389`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `962285cbd9442dc6ffaecfb1865470001cc4ea9b9b35debb8d3c3807f610b4c8`  
**Date:** October 2026

## Teaching with CYCLON_P2P

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `962285cbd9442dc6ffaecfb1865470001cc4ea9b9b35debb8d3c3807f610b4c8` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
