# .gmem Format Overview

**Version:** 1.0  
**Date:** 2026-08-20  
**Status:** Public Specification  
**Owner:** graph-memory-core  
**Related ADR:** ADR-002 (File Format - .gmem vs .cgraph), ADR-006 (Portability Requirements)

## Purpose

Define the portable, self-contained file format used by Graph Memory Core.

`.gmem` is the generic storage format for the Graph Memory Core engine.
It is intentionally domain-agnostic: it knows only about entities, relations,
events, commits, and snapshots.

## Design Principles

| Principle | Rationale |
|---|---|
| **Portable** | A `.gmem` file must work across installations and versions (ADR-006) |
| **Self-contained** | Schema is embedded in the file; no external dependencies |
| **Human-readable** | Structured text representation aids debugging and inspection |
| **Versioned** | Each file carries its own schema version for safe migration |
| **Generic** | No domain concepts leak into the format (ADR-001) |

## High-Level Structure

```
.gmem file
├── Header (metadata, schema version)
├── Schema (embedded type definitions)
├── Event Stream (source of truth)
├── Commits (snapshots / checkpoints)
└── Context Layer (human commentary, separated from facts)
```

### Header

```yaml
format: gmem
version: 1
schema_version: 1
created_at: 2026-08-20T00:00:00Z
generator: graph-memory-core/1.0
```

### Schema

Embedded type definitions describing the entities and relations present
in the file. Allows consumers to validate and interpret the graph without
external schema references.

### Event Stream

The source of truth. Every state change is recorded as an event
(see ADR-005: Event Sourcing Model).

```
Event Stream → Graph Projection → Current State
```

Example events:
- `EntityCreated`
- `EntityUpdated`
- `RelationshipCreated`
- `RelationshipDeleted`
- `EventRecorded`

### Commits

Snapshots / checkpoints that enable diff and evolution tracking
(see ADR-009: Graph Commit Model).

- **Commit** = snapshot checkpoint
- Enables **graph diff** — see what changed between commits
- Tracks evolution over time
- Supports rollback and replay

### Context Layer

Human commentary separated from objective facts
(see ADR-007: Human Context Layer Separation).

- **Facts** — objective, structured data
- **Context** — subjective interpretation

## Portability

Per ADR-006, a `.gmem` file must:

- Embed its own schema (no external schema lookup)
- Carry a schema version for forward/backward compatibility
- Have no runtime dependencies on a specific installation version
- Migrate freely between installations

## Versioning Concepts

- File version identifies format version
- Schema version identifies type definitions version
- Compatible readers must handle schema evolution

## Compatibility Principles

- Backward compatibility: newer readers can read older files
- Forward compatibility: readers should fail gracefully on unknown versions
- Schema evolution must be documented
- Migration path for deprecated schema versions

## Relationship to Other Formats

| Format | Scope | Status |
|---|---|---|
| `.gmem` | Generic Graph Memory Core storage | **Active** |
| `.cgraph` | Domain-specific (CareerGraph) | **Deprecated** — see ADR-002 |

Domain applications must map their native format to `.gmem` before
exchanging data with the core engine.

## References

- `ADRs/ADR-002.md` — File Format separation
- `ADRs/ADR-005.md` — Event Sourcing Model
- `ADRs/ADR-006.md` — Portability Requirements
- `ADRs/ADR-007.md` — Human Context Layer Separation
- `ADRs/ADR-009.md` — Graph Commit Model

**Owner:** graph-memory-core  
**Next revision:** when commit/snapshot format is concretely specified
