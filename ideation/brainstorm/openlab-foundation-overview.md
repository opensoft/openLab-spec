# openLab Initial Foundation Overview — Brainstorm

Status: brainstorm
Kind: reference
Summary: Provide neutral laboratory contracts and synthetic conformance examples in a public triad.
Topics: openlab-foundation, laboratory-architecture, contracts
Repository context: Opensoft/openLab public triad; neutral interfaces and synthetic examples.
Captured: 2026-11-08

## Possible feats

- **Draft foundation release** — Establish independently usable contract definitions and examples for instrument integration and data ingestion.

## Motivation

Instrument control, raw acquisition data and laboratory applications need explicit boundaries. A portable foundation should work without requiring a particular commercial application or vendor SDK.

## Goals

Define strict initial payloads, explain lifecycle/recovery semantics, expose limits and provide executable synthetic examples.

## Non-goals

No equipment control, validated assay, proprietary raw-format parser, production importer, SDK or analysis engine is delivered. These documents are brainstorms; schemas are draft interfaces. No business application architecture or private product source is included.

## What the system delivers

Common scope/references, Zeus rotation/slot-position requests, execution status/evidence, HPLC/MS file-import requests and raw artifact metadata. The code leg supplies fixtures and offline schema/integrity checks.

## System model

Application authorizes work -> host validates capability/profile -> driver or importer performs technical work -> evidence returns -> application owns scientific acceptance and reporting. Broker and storage implementations can vary. Neither private dependencies nor AI services are required.

## Cluster map

- [Joint examples](openlab-foundation-synthesis-examples.md) connects command, import and packaging boundaries.

## How it fits

The spec leg owns schemas and exploratory design. The code leg owns executable fixtures/checks. Assembly pins select exact versions. Future SDKs and adapters implement these contracts after review and qualification.

## Key decisions and open questions

Focus means slot positioning, not optical autofocus. File import does not imply HPLC control. Host/business responsibilities remain outside reusable drivers. Namespace hosting, licensing, capability discovery/lifecycle schemas and real hardware/vendor profiles remain open.

## Document map

- [Commands](openlab-foundation-commands.md)
- [File import](openlab-foundation-file-import.md)
- [Structure](openlab-foundation-structure.md)
- [Synthesis](openlab-foundation-synthesis-examples.md)
