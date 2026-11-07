# CYCLON_P2P

> cyclon.p2p A Javascript implementation of the Cyclon peer sampling protocol

**Category:** ARTIST_TOOLS · **Ecosystem:** unknown · **Vendored upstream:** https://github.com/nicktindall/cyclon.p2p · **Pinned commit:** `75866f03fd9bb7de0abde920bd4761660de5a389` · **Vendor:** Anticloud FZ LLE

## What This Project Is

cyclon.p2p A Javascript implementation of the Cyclon peer sampling protocol

This is the upstream project, vendored at the pinned commit above and packaged offline-first. The 12 improvements Anticloud adds live in `anticloud/` and are described under *Anticloud Overlay* below. Every fact in this file traces to a file in this directory.

## Installation

```
# See the upstream README (linked above) for build steps.
```

## Usage

See the upstream README (linked above) for usage. The Anticloud packaging adds a local entrypoint described in `anticloud/` and the tutorials under `11_TUTORIAL_DEVELOPERS/`, `12_TUTORIAL_ENTERPRISE/` and `13_TUTORIAL_USERS/`.

## Anticloud Overlay

The 12 improvements live under `anticloud/`. Run the check suite from this directory:

```
python anticloud/bench/runner.py --cwd anticloud
```

## Benchmark Results

The suite is recorded in `BENCH.json`; no benchmark rows were found in this package.

## Licence

The upstream licence is preserved in `LICENSE` and `THIRD_PARTY_LICENSES/`. The Anticloud overlay is licensed under Anticommons 0.1.0 (`ANTICOMMONS_LICENSE.md`).

## Verification

SHA3-256 of `BENCH.json`:

```
7204ca430a59ab05b3221c4cbcb5052da3625772f39203a33ec8b4074a7d37d2
```

Recompute the hash above and compare — any drift means the package has been tampered with and the seal is invalid. This is a self-assessment; no external audit has been performed and a SOC 2 / NIST independent audit is committed post-funding.
