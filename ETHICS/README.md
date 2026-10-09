# Ethics — CYCLON_P2P

**Project:** CYCLON_P2P  
**Category:** SOCIAL_MEDIA  
**Upstream:** https://github.com/nicktindall/cyclon.p2p  
**Pinned commit:** `75866f03fd9bb7de0abde920bd4761660de5a389`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `962285cbd9442dc6ffaecfb1865470001cc4ea9b9b35debb8d3c3807f610b4c8`  
**Date:** October 2026

## Position

CYCLON_P2P is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
