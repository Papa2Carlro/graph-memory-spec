# Graph Memory Overview

**Version:** 1.0  
**Date:** 2026-08-20  
**Status:** Public Documentation  
**Owner:** Architecture Team  

---

## What is Graph Memory?

**Graph Memory** is a platform for living knowledge models. It provides a structured way to represent,
evolve, and reason about knowledge graphs that capture entities, relationships, and their evolution over time.

Unlike static databases, Graph Memory supports:
- **Event sourcing** — all changes are recorded as events
- **Graph projections** — the current graph state is a projection from the event stream
- **Commit-based history** — snapshots enable diff and evolution tracking
- **Portable file format** — `.gmem` files can migrate between installations

### Core Philosophy

> **Human-first, AI-assisted.** Graph Language is designed for human authorship first, with AI as a
> Copilot for creating, explaining, and verifying knowledge models.

---

## Architectural Layers

Graph Memory consists of four primary layers, each with a distinct responsibility:

### 1. Core Layer (`graph-memory-core`)

**Role:** Generic engine infrastructure.

Provides the foundational primitives for graph memory operations:

- **Storage format** — `.gmem` binary/structured format
- **Event sourcing** — event stream as source of truth
- **Commit/snapshot model** — versioned graph history
- **Portability** — `.gmem` files work across installations
- **Fact vs Context separation** — objective data vs subjective interpretation

**Does NOT know about:**
- Vacancies, CVs, salaries
- Specific domains (career, assets, docs)
- UI workflows

**Knows only:**
- Entities, Relations
- Events (SkillCreated, ProjectCreated, etc.)
- Graph structure

```
Graph Memory Core
        |
        +→ .gmem format
        +→ Event stream
        +→ Commits/Snapshots
        +→ Fact/Context layering
```

### 2. Language Layer (`graph-memory-language`)

**Role:** Graph Language — human-first DSL for authoring knowledge models.

- **Syntax** optimized for human readability
- **Compiler** handles optimization and translation to .gmem
- **Domain experts** can write directly without programming knowledge
- **AI-assisted** — Copilot-like support for writing, explaining, verifying

**Purpose:** Enable humans to describe knowledge graphs naturally.

```
Human → Graph Language → Graph Compiler → .gmem → Graph Runtime
```

### 3. MCP Layer (`graph-memory-mcp`)

**Role:** Model Context Protocol — two-level tool architecture.

**Two-level split:**

- **Core MCP tools** (generic graph operations):
  - `query_graph()`
  - `create_entity()`
  - `add_event()`
  - `get_snapshot()`

- **Domain MCP tools** (application-specific):
  - Career workflow tools
  - Vacancy matching tools
  - Profile generation tools

**Purpose:** Clean separation between generic graph tools and application-specific tools.

```
AI Agent
        |
        ↓
   MCP
        |
+---------+----------+
|                    |
↓                    ↓
Graph Memory Tools    Domain Tools
(core layer)         (CareerGraph layer)
```

### 4. Application Layer

**Role:** Domain-specific applications built on top of Graph Memory.

**Examples:**
- **CareerGraph** — career knowledge model, vacancy matching, profile management
- **DocGraph** — document knowledge model
- **ProjectGraph** — project tracking, evidence management

**Application layer knows about:**
- Domain-specific entities and relationships
- UI workflows, business logic
- Career domains, vacancy data

**Does NOT modify core layer** — uses public API only.

```
Application (CareerGraph, DocGraph, etc.)
        |
        ↓
   MCP (Domain Tools)
        |
        ↓
   MCP (Core Tools)
        |
        ↓
   Graph Memory Core
        |
        ↓
   .gmem Format
```

---

## Key Concepts

### Event Sourcing

The graph state is derived from an **event stream**, not stored directly.

```
Event Stream → Graph Projection → Current State
```

**Events** (examples):
- `SkillCreated`
- `ProjectCreated`
- `EvidenceAdded`
- `DecisionRecorded`
- `RelationshipCreated`

**Benefits:**
- All changes are auditable
- Enable time-travel and diff
- No hidden state

### Commit / Snapshot Model

Graph supports **commit-based history** similar to Git.

- **Commit** = snapshot checkpoint
- Enables **graph diff** — see what changed between commits
- Tracks **career evolution** over time
- Supports rollback and replay

### File Format: `.gmem`

**Generic storage format** for Graph Memory Core.

- **Portable** between installations
- **Schema embedded** in file
- **No external dependencies**
- Can migrate between CareerGraph installations

**Not to be confused with:**
- `.cgraph` — domain-specific format (deprecated/conflated)

### Fact vs Context Layer

- **Facts** — objective, structured data: Project, Technology, Skill
- **Context** — subjective interpretation: migration difficulty, leadership growth, career moments

This separation enables:
- Flexible human commentary without polluting data
- Multiple interpretations of same facts
- Clean data model for machine reasoning

---

## Role Summary

| Layer | Responsibility | Knows About |
|-------|---------------|-------------|
| **Core** | Engine, format, events, portability | Entities, Relations, Events |
| **Language** | Human-first DSL, compiler | Syntax, semantics, compilation |
| **MCP** | Two-level tool split | Core tools, Domain tools |
| **Application** | Domain-specific logic | Domain entities, UI, workflows |

---

## Getting Started - New Developer

1. **Read this overview** — understand the four-layer architecture
2. **Explore graph-memory-core** — understand the engine and .gmem format
3. **Learn Graph Language** — human-first DSL for authoring
4. **Understand MCP** — two-level tool architecture
5. **Build an application** — CareerGraph, DocGraph, or custom

**Entry points:**
- `graph-memory-core/README.md` — Core engine details
- `graph-memory-language/` — Language design and compiler
- `graph-memory-mcp/` — MCP tool architecture
- `ADRs/` — Architectural decision records
- `GRAPH_MEMORY_OVERVIEW.md` — This document

---

## References

- DECISION_REGISTRY.md — All accepted architectural decisions
- ADR-001 through ADR-011 — Specific decisions with rationale
- graph-memory-core/ — Core engine repository
- graph-memory-language/ — Graph Language repository
- graph-memory-mcp/ — MCP architecture repository