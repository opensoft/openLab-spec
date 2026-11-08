# Public Triad Project Structure — Brainstorm

Status: brainstorm
Kind: architecture
Summary: Keep contract definitions in the spec leg and executable examples in the code leg.
Topics: openlab-foundation, project-structure, packaging
Repository context: Opensoft/openLab public triad; neutral interfaces and synthetic examples.
Captured: 2026-11-08

## Possible feats

- **Independent foundation** — Grow SDKs and adapters from interoperable contracts and useful conformance examples.

## Current structure

```text
openLab/                         assembly root: manifest, pins, shape validation
  spec/                         openLab-spec submodule
    contracts/v0.1/             JSON Schema draft 2020-12 definitions
    ideation/brainstorm/        exploratory design packet
  code/                         openLab-code submodule
    examples/zeus/              synthetic typed requests
    examples/hplcms/            synthetic files and matching manifest
    tools/check_examples.py     offline schema/integrity checks
    tests/                     invalid-input and integrity cases
```

Schema IDs use a proposed stable namespace; schemas are resolved locally and no hosted schema endpoint is promised. Schema package version is draft 0.1.0. This is exploratory, not a ratified release. Future incompatible execution semantics require a new major version; unknown operations/parameters reject rather than silently downgrade.

## Growth path

Add .NET/Dart bindings for real consumers, capability discovery schemas, durable command/import hosts, concrete adapters, artifact stores and analysis workers when justified. Do not scaffold empty projects for symmetry. Keep SDKs transport-neutral; drivers encode device protocols, hosts manage connection/authorization/local serialization, and applications own laboratory workflows and records.

All public examples run without private repositories, credentials or physical equipment. Multiple code packages can remain in the code leg. Split independently maintained adapters only for concrete release/licensing needs. A file importer is not an HPLC control driver.

## Cross-leg consumption

The checker accepts --contracts or CONTRACTS_DIR; the default is the assembly's spec/contracts/v0.1 mount. Definitions remain in the spec leg rather than being copied into code. Code CI checks out the public spec repository at an exact commit, independent of mutable main. Root pin updates use the shape tooling, never hand-edited digests.

## Alternatives and open questions

SDK/package names, public license and vendor publication rights remain separate decisions. No license is selected by this packet; public visibility alone is not an open-source license grant.

## Relationships

See [commands](openlab-foundation-commands.md), [import](openlab-foundation-file-import.md), and [joint examples](openlab-foundation-synthesis-examples.md).
