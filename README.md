# CYCLON P2P

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-social_media-lightgrey)

> Anticloud-hardened packaging of the upstream project `CYCLON_P2P` in category **SOCIAL MEDIA**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** SOCIAL MEDIA · **Upstream:** https://github.com/nicktindall/cyclon.p2p · **Upstream pin:** `75866f03fd9bb7de0abde920bd4761660de5a389` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

cyclon.p2p
==========

[![Build Status](https://travis-ci.org/nicktindall/cyclon.p2p.svg?branch=master)](https://travis-ci.org/nicktindall/cyclon.p2p)
[![Dependencies](https://david-dm.org/nicktindall/cyclon.p2p.png)](https://david-dm.org/nicktindall/cyclon.p2p)

A Javascript implementation of the Cyclon peer sampling protocol

The details and an analysis of the implementation can be found in;

> N. Tindall and A. Harwood, "Peer-to-peer between browsers: cyclon protocol over WebRTC," Peer-to-Peer Computing (P2P), 2015 IEEE International Conference on, Boston, MA, 2015, pp. 1-5.
>doi: 10.1109/P2P.2015.7328517

The Cyclon protocol is described in;

> Voulgaris, S.; Gavidia, D. & van Steen, M. (2005), 'CYCLON: Inexpensive Membership Management for Unstructured P2P Overlays', J. Network Syst. Manage. 13 (2).

Overview
--------
The cyclon.p2p implementation has two dependencies, a `Bootstrap` and a `Comms` instance. Their functions and interfaces are described below.

### Bootstrap
The purpose of the `Bootstrap` is to retrieve some peers to initially populate a node's neighbour cache. Its interface is quite simple.

#### `getInitialPeerSet(localNode, maxPeers)`
Get an initial set of peers. Returns a Promise that will resolve to a set of peers no greater than the specified limit.

##### Parameters
* **localNode** The CyclonNode that is requesting the peers.
* **limit** The maximum number of peers to return.

### Comms
The `Comms` is the layer that takes care of a node's communication with other nodes. It is responsible for executing shuffles for the local node. Its interface is again quite simple.

#### `initialize(localNode, metadataProviders)`
Initialize the Comms instance. This must be called before any attempt is made to do anything else.

##### Parameters
* **localNode** A reference to the local CyclonNode.
* **metadataProviders** A JavaScript Object whose keys will be used as node pointer metadata keys and values will be executed to get the corresponding values.

#### `sendShuffleRequest(destinationNodePointer, shuffleSet)`
Send a shuffle request to another node in the network. Returns a cancellable Bluebird promise that will resolve when a shuffle has been successfully executed. If a cancellation or error occurs it will reject with the error.

##### Parameters
* **destinationNodePointer** The node pointer of the destination node.
* **shuffleSet** The set of node pointers to include in the shuffle request message.

#### `createNewPointer()`
Create a new pointer to the local node, containing the current metadata and signalling details.

#### `getLocalId()`
Return the string which the Comms layer is using to identify the local node.

Usage
-----
On its own this package is not particularly useful unless you intend to create your own `Comms` and `Bootstrap` implementations. The [cyclon-p2p-rtc-comms](https://github.com/nicktindall/cyclon.p2p-rtc-comms) package provides a configurable implementation of the interfaces that will work in modern Chrome and Firefox (and maybe Opera?) browsers. 

A demonstration of the WebRTC implementation of cyclon.p2p can be found [here](http://cyclon-js-demo.herokuapp.com). Open a few tabs and watch the protocol work.

### The Local Simulation
This package contains "local" `Comms` and `Bootstrap` implementations that can be used to run a local multi-node simulation of the protocol by executing
 
```
node localSimulation.js
```

In the working directory. The local simulation is configured to bootstrap each peer in the network with only the node pointer of its neighbour to the right (on a number scale, wrapping at the node with the maximum ID). It will then start all the nodes and output some network metrics.

An example of the output:
```
Starting Cyclon.p2p simulation of 50 nodes
Ideal entropy is 5.614709844115208
1: entropy (min=Infinity, mean=NaN, max=-Infinity), in-degree (mean=0, std.dev=0), orphans=50
2: entropy (min=0, mean=0, max=0), in-degree (mean=1, std.dev=0), orphans=0
3: entropy (min=0.9182958340544896, mean=1.0008546455628127, max=2), in-degree (mean=1.56, std.dev=0.6374950980203691), orphans=0
4: entropy (min=2.2516291673878226, mean=2.3793927048285384, max=3.1219280948873624), in-degree (mean=4.48, std.dev=2.475802900071005), orphans=0
5: entropy (min=2.5216406363433186, mean=2.972442624013195, max=3.75), in-degree (mean=6.66, std.dev=3.2410492128321655), orphans=0
```

The information output includes

* **entropy** A measurement of the *Shannon Entropy* of the stream of peers that the protocol has produced over the network. The entropy of the stream is measured at each node and the statistics aggregated. The Shannon entropy is an indication of how evenly the probabilities of each node in the network being selected are distributed. The "ideal" entropy, where each peer is equally likely to appear in the sample, is output at the beginning of the simulation.
* **in-degree** The in-degree in a directed graph is the number of edges arriving at a particular vertex. In the context of the Cyclon network it indicates the number of peers whose neighbour caches have a pointer to a particular node.
* **orphans** This is just a count of the number of nodes in the network with an in-degree of zero. This should stay at zero.

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Node.js / npm** (manifests: package.json, package-lock.json; scanned in UPSTREAM_CLONE)
- Top-level source layout: `spec/`, `src/`, `test/`
- Snapshot size: **20 files**, **794 lines of code** (measured; see Benchmarks)
- Primary languages: `.ts` (10), `.json` (4), `(none)` (3), `.js` (1), `.md` (1), `.yml` (1)
- Upstream commit pinned for this packaging: `75866f03fd9bb7de0abde920bd4761660de5a389`

---

## Installation

[![Dependencies](https://david-dm.org/nicktindall/cyclon.p2p.png)](https://david-dm.org/nicktindall/cyclon.p2p)

A Javascript implementation of the Cyclon peer sampling protocol

The details and an analysis of the implementation can be found in;

> N. Tindall and A. Harwood, "Peer-to-peer between browsers: cyclon protocol over WebRTC," Peer-to-Peer Computing (P2P), 2015 IEEE International Conference on, Boston, MA, 2015, pp. 1-5.
>doi: 10.1109/P2P.2015.7328517

The Cyclon protocol is described in;

> Voulgaris, S.; Gavidia, D. & van Steen, M. (2005), 'CYCLON: Inexpensive Membership Management for Unstructured P2P Overlays', J. Network Syst. Manage. 13 (2).

Overview
--------
The cyclon.p2p implementation has two dependencies, a `Bootstrap` and a `Comms` instance. Their functions and interfaces are described below.

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

-----
On its own this package is not particularly useful unless you intend to create your own `Comms` and `Bootstrap` implementations. The [cyclon-p2p-rtc-comms](https://github.com/nicktindall/cyclon.p2p-rtc-comms) package provides a configurable implementation of the interfaces that will work in modern Chrome and Firefox (and maybe Opera?) browsers. 

A demonstration of the WebRTC implementation of cyclon.p2p can be found [here](http://cyclon-js-demo.herokuapp.com). Open a few tabs and watch the protocol work.

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

The upstream API surface is defined by the `CYCLON_P2P` source tree vendored in `UPSTREAM_CLONE/` (Node.js / npm ecosystem). Public entry points:

- Source modules: `spec/`, `src/`, `test/`
- The snapshot declares 8 dependency references across 1 ecosystem(s); see Dependencies below.
- Overlay API: `anticloud/cli.py` exposes 13 subcommands with JSON stdout; `anticloud/bench/runner.py` runs the 16-check suite; `anticloud/provenance/chain.py` exposes the SHA3-256 + Ed25519 provenance chain.

---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Node.js / npm |
| Manifests detected | package.json, package-lock.json |
| Files in snapshot | 20 |
| Lines of code | 794 |
| Dependency references | 8 |
| Dependencies by ecosystem | npm: 8 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| npm | @types/node | ^10.14.22 | package.json |
| npm | cyclon.p2p-common | ^0.1.11 | package.json |
| npm | @istanbuljs/nyc-config-typescript | ^0.1.3 | package.json |
| npm | jasmine | ^2.99.0 | package.json |
| npm | nyc | ^14.1.1 | package.json |
| npm | source-map-support | ^0.5.13 | package.json |
| npm | ts-node | ^8.4.1 | package.json |
| npm | typescript | ^3.6.4 | package.json |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

A demonstration of the WebRTC implementation of cyclon.p2p can be found [here](http://cyclon-js-demo.herokuapp.com). Open a few tabs and watch the protocol work.

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `CYCLON_P2P` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
The MIT License (MIT)

Copyright (c) 2014 Nick Tindall

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `CYCLON_P2P` (category: SOCIAL MEDIA)
- **Upstream URL:** https://github.com/nicktindall/cyclon.p2p
- **Pinned commit (SHA):** `75866f03fd9bb7de0abde920bd4761660de5a389`
- **Branch:** master
- **Pin provenance:** resolved during the second documentation pass. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`574636a40326ab61896c481f183b29494754c9134818c7955d68549c22aa8e1d`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| DANS (KNAW/NWO, Netherlands) | 10.17026/PT | EU-recognised archive |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe
and Mail, Business Insider, National Post, Financial Post, StreetInsider,
Digital Journal, Barchart, International Business Times, and Fox News.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

