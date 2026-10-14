# Technical Architecture — CYCLON_P2P

**Upstream:** [https://github.com/nicktindall/cyclon.p2p](https://github.com/nicktindall/cyclon.p2p)
**License:** MIT
**Category:** SOCIAL_MEDIA
**Anticloud Integration:** PAX L5 Narrow L2 General 27B + AIOSS + Offline-First

## Upstream Description

P2P social graph layer

## Anticloud Architectural Changes

1. PAX L5 Narrow L2 General 27B local content moderation — no third-party NLP APIs
2. AIOSS append-only post and moderation audit chain
3. AES-256 end-to-end encryption for all direct messages
4. Single-binary self-hosted instance — no cloud provider required
5. Zero-cloud: ActivityPub federation with fully local infrastructure
6. GPU/CPU equalizer: moderation inference scales to available hardware
7. Zero-telemetry: removes all ad tracking and behavioral profiling
8. Open data export: full user data portability in standard formats

## Integration Points

- **PAX Inference Socket:** Local HTTP endpoint at `127.0.0.1:11434/v1/chat` — same OpenAI-compatible API, zero cloud
- **AIOSS Hook:** Every write operation calls `aioss_append(event, payload)` before commit
- **Encryption Layer:** All file I/O routed through `anticloud_crypto.encrypt_at_rest()`
- **Single Binary Build:** `pyinstaller anticloud_cyclon_p2p.spec` or `go build -o cyclon_p2p`

## Deployment Modes

| Mode | Hardware | Notes |
| --- | --- | --- |
| Edge CPU | Raspberry Pi 4 / Intel NUC | Full feature set, PAX on CPU |
| Desktop GPU | RTX 3060 / A10 | PAX GPU inference, <1s latency |
| Server | 2× A100 | Full batch throughput |
| Air-gapped | Any x86/ARM | Zero network dependency |