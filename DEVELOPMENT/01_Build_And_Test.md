# Build and Test

**Project:** `CYCLON_P2P`
**Upstream:** https://github.com/nicktindall/cyclon.p2p
**License:** MIT

## Quick Start

```bash
git clone https://github.com/nicktindall/cyclon.p2p
cd cyclon.p2p
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local content moderation — no third-party NLP APIs
2. AIOSS append-only post and moderation audit chain
3. AES-256 end-to-end encryption for all direct messages
4. Single-binary self-hosted instance — no cloud provider required
5. Zero-cloud: ActivityPub federation with fully local infrastructure
6. GPU/CPU equalizer: moderation inference scales to available hardware
7. Zero-telemetry: removes all ad tracking and behavioral profiling
8. Open data export: full user data portability in standard formats

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.
