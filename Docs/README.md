# Graph Memory Specification — Documentation Entry Point

Public specification repository for the Graph Memory ecosystem.

## Purpose

This repository is the **single source of truth** for public architectural
decisions, specifications, and the decision registry of Graph Memory. It contains
no implementation code — only formal records that other repositories reference.

## Documentation Map

```
Docs/
├── README.md                          ← this file
├── GRAPH_MEMORY_OVERVIEW.md           # Architectural overview & layers
├── DECISION_REGISTRY.md               # Registry of all accepted ADRs
├── ADR_VALIDATION_REPORT.md           # ADR validation & implementation gaps
├── DOCUMENTATION_MIGRATION_PLAN.md    # Cross-repository migration plan
├── ADRs/
│   ├── ADR-001.md  Core vs Product Separation
│   ├── ADR-002.md  File Format - .gmem vs .cgraph
│   ├── ADR-003.md  Two-Level MCP Architecture
│   ├── ADR-004.md  Graph Language Human-First Philosophy
│   ├── ADR-005.md  Event Sourcing Model
│   ├── ADR-006.md  Portability Requirements
│   ├── ADR-007.md  Human Context Layer Separation
│   ├── ADR-008.md  Agent Permission Model
│   ├── ADR-009.md  Graph Commit / Snapshot Model
│   ├── ADR-010.md  Rules vs Workflows Separation
│   ├── ADR-011.md  Repository Structure Proposal
│   └── ADR-012_Schema_Architecture_Decision.md  Schema Architecture Decision
├── Formats/
│   └── GMEM_FORMAT_OVERVIEW.md       # Overview of .gmem format concepts and portability principles
└── planning/
    ├── MIGRATION_REPORT.md            # Phase 1 migration report
    └── DOCUMENTATION_MIGRATION_EXECUTION_PLAN.md
```

## Where to Start

| If you want to… | Read |
|---|---|
| Understand the architecture | `GRAPH_MEMORY_OVERVIEW.md` |
| See all accepted decisions | `DECISION_REGISTRY.md` |
| Understand a specific decision | `ADRs/ADR-001.md` … `ADR-011.md` |
| Know the file format | `Formats/GMEM_FORMAT_OVERVIEW.md` |
| Know what is validated / open | `ADR_VALIDATION_REPORT.md` |
| Understand how docs are organized | `DOCUMENTATION_MIGRATION_PLAN.md` |

## Related Repositories

| Repository | Layer | What it owns |
|---|---|---|
| `graph-memory-core` | Core engine | Core runtime implementation, event sourcing, storage and graph execution |
| `graph-memory-spec` | Specification | Public contracts, ADRs, .gmem format specification |
| `graph-memory-language` | Language | Graph Language DSL, compiler, type system |
| `graph-memory-mcp` | MCP integration | Two-level MCP tools, permissions, agents |
| `graph-memory-cli` | CLI | Command-line tooling |
| `careerhub` | Product | CareerGraph application layer |

## Source of Truth Boundaries

- **This repository owns** the public architectural record: ADRs, the decision
  registry, validation report, and the `.gmem` format specification.
- **ADRs are immutable.** Once accepted they are never modified for migration or
  refactoring purposes. Clarification is handled via a new ADR or amendment.
- **No duplication.** Each document lives in exactly one canonical location.
  Other repositories reference this one rather than copying content.
- **Source documents** referenced by ADRs remain in their original location
  (`careerhub/Docs/`); this registry indexes them, it does not duplicate them.
- **Migration plans** live in `Docs/planning/` and describe process, not
  architecture. They introduce no new architectural decisions.