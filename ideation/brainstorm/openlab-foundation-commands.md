# Instrument Capability and Command Boundary — Brainstorm

Status: brainstorm
Kind: architecture
Summary: Describe technical operations independently of laboratory business records and transport bindings.
Topics: openlab-foundation, contracts, commands
Repository context: Opensoft/openLab public triad; neutral interfaces and synthetic examples.
Captured: 2026-11-08

## Possible feats

- **Portable instrument interface** — Implement the same typed operations in simulators and qualified device adapters.

## Initial vocabulary

Scope identifies an organization/laboratory; instrumentId identifies equipment within scope. Neither field authorizes a caller. The host validates authenticated identity and policy. External references link owning records without copying patient or experiment schemas. Component identity includes an immutable build digest.

Capability descriptors identify a revision and operation parameter constraints, configured slot count, supported modes, completion-evidence basis and recovery rules. Availability is a timestamped observation separate from support. Descriptor discovery schema is deferred; command requests reference an exact descriptor revision. Hosts must validate that revision, configuration, expiry and readiness before dispatch.

## Zeus example

turntable.rotate accepts exactly one mode: relative-degrees with a finite signed angle or absolute-degrees in [0,360) with a known coordinate reference. turntable.position-slot takes slotNumber from 1 through the configured slot count. “Focus” in this example means alignment of a slot with the viewing position, not optical autofocus. Device-specific limits, homing and interlocks remain authoritative. No camera, eject/load or speed-control capability is implied.

See [command request schema](../../contracts/v0.1/command-request.schema.json) and [execution schema](../../contracts/v0.1/command-execution.schema.json). The execution schema is an initial status/evidence projection, not a full production audit record.

## Identity and completion

Stable requestId is scoped by lab/instrument. Same identity and canonical execution payload returns the same execution; different content conflicts. Durable acceptance precedes dispatch. Verify device-side deduplication too; no exactly-once physical guarantee is asserted. Retain identities through the supported replay horizon.

accepted -> running -> succeeded/failed/indeterminate; an accepted but undispatched request can be rejected. A timeout after dispatch may be indeterminate. Reconcile before a new physical action; failed may include partial motion. No generic cancellation/stop is promised. Every update increments statusRevision; duplicate/out-of-order messages cannot roll back status. A synchronous pre-acceptance rejection returns an error rather than claiming execution.

Published or accepted is not completed. Evidence distinguishes device-observed, adapter-inferred and no-op outcomes. Host audit retains request/configuration fingerprint, timestamps, caller and reconciliation history outside this first projection. Core execution contracts do not require an AI runtime or a specific message broker.

## Alternatives and open questions

Schema validation alone cannot check physical readiness, authorization, descriptor compatibility or replay state. A real adapter needs qualification against its firmware/configuration. Initial public examples are synthetic and issue no commands.

## Relationships

See [joint examples](openlab-foundation-synthesis-examples.md) and [structure](openlab-foundation-structure.md).
