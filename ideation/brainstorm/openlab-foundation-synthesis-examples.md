# Synthesis: Positioning and Raw File Import — Brainstorm

Status: brainstorm
Kind: architecture
Summary: Use two independently testable examples to separate physical execution from evidence ingestion.
Topics: openlab-foundation, synthesis, zeus, hplc-ms
Repository context: Opensoft/openLab public triad; neutral interfaces and synthetic examples.
Captured: 2026-11-08

## Possible feats

- **Initial conformance slice** — Exercise strict command shapes and file integrity without equipment or proprietary data.

## Members and their joints

Join [commands](openlab-foundation-commands.md), [file import](openlab-foundation-file-import.md) and [structure](openlab-foundation-structure.md).

## Sequence and authority

For positioning, a host authorizes a technical request, validates advertised capability and device readiness, then executes through one local scheduler/driver. It reports observed or uncertain outcomes. The public checker validates request structure only; it does not execute this sequence.

For import, a host authorizes a source/profile, establishes trusted acquisition completion, stages/validates bytes and registers evidence. The public checker validates static files and hashes only. Acquisition completion, material identity, scientific analysis and release are distinct decisions.

## Emergent behavior

The same neutral scope, reference and version vocabulary supports physical action and data movement while preserving their different recovery rules. Retrying file verification must never trigger another acquisition. Neither operation requires a business database or AI runtime.

## Tensions to hold

Schemas cover payload shape; hosts enforce authorization, temporal validity, dynamic capabilities, durable idempotency and device interlocks. Small synthetic files prove fixture integrity, not vendor compatibility or production transfer safety.

## Recombination opportunities

Reuse artifact contracts for GC/MS or microscopy, and positioning interfaces for qualified compatible turntables. Analysis engines may later consume the immutable artifacts through a separate contract.

## Open questions

Select a first hardware qualification target and real vendor import profile after the neutral contracts are reviewed.
