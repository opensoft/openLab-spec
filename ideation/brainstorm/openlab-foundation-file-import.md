# Raw Acquisition Import Boundary — Brainstorm

Status: brainstorm
Kind: architecture
Summary: Register completed raw file bundles without claiming instrument control or scientific interpretation.
Topics: openlab-foundation, contracts, artifact-import, provenance
Repository context: Opensoft/openLab public triad; neutral interfaces and synthetic examples.
Captured: 2026-11-08

## Possible feats

- **Vendor-neutral ingestion** — Preserve immutable acquisition evidence before a vendor-specific reader is available.

## Import model

The [import request](../../contracts/v0.1/import-request.schema.json) names a configured profile, source system/run identity, file manifest and completion evidence. The profile resolves permitted roots/limits and trusted operator confirmation or vendor marker. Caller text alone does not prove completion. No arbitrary source root, credentials or permanent signed URLs belong in the request.

The [artifact schema](../../contracts/v0.1/artifact.schema.json) represents registered raw evidence using file sizes/hashes, a manifest digest, acquisition identity and a provider-neutral storage reference. Unknown format can be recorded explicitly; preserving bytes does not establish analysis compatibility. Source instrument/method/acquisition time should carry origin and verification status when added.

## Integrity and recovery

Reserve source identity within scope. Same identity/digest deduplicates; same identity/different bytes conflicts without overwrite. Distinct injections remain distinct even with identical bytes. Never infer patient/sample identity from filenames. The owning application retains material associations and approval decisions.

Reject traversal, absolute paths, symlink escapes and duplicate/case-colliding normalized paths. Stage, hash, recheck source stability and durably register before publication. Do not execute imported content or unpack untrusted archives automatically. Failed/incomplete imports are not available acquisitions. Production execution must prevent concurrent source mutation and path replacement; the static fixture checker does not claim those guarantees.

Proposed importer lifecycle: accepted -> validating -> transferring -> verifying -> available, with failed/conflict records and linked recovery attempts. available means durable raw evidence, not analyzed, scientifically accepted or released. ImportRun/AcquisitionRecord lifecycle schemas and durable catalog implementation are deferred.

## HPLC/MS example

The code leg contains a tiny synthetic export bundle with real matching hashes. It validates the manifest and bytes offline. It neither reads proprietary vendor formats nor operates equipment. A later analysis request can reference immutable artifacts, exact pipeline/engine versions, parameters and reference data; result review/release remains an application responsibility.

## Alternatives and open questions

Choose vendor completion signals and source-key rules per import profile. A quiet directory alone is insufficient. Retention, access policy and clinical/research interpretation are host concerns, not file-integrity checks.

## Relationships

See [joint examples](openlab-foundation-synthesis-examples.md) and [structure](openlab-foundation-structure.md).
