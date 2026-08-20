# Decision Registry

**Version:** 1.0  
**Date:** 2026-08-20  
**Status:** Registry of accepted architectural decisions

## Purpose

Central registry of all accepted architectural decisions for Graph Memory ecosystem. Serves as single source of truth for decision history and rationale.

---

## ADR-001: Core vs Product Separation

**ID:** ADR-001  
**Title:** Core vs Product Separation  
**Status:** ACCEPTED  
**Implementation Status:** Defined  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-core  
**Summary:** Graph Memory Core is private infrastructure layer, CareerGraph is open source product. Separation ensures generic engine can support multiple domains.  
**Source Documents:**
- `careerhub/Docs/Graph_Memory_Architecture_Decision.md`
- `careerhub/Docs/Graph_Memory_Separation_Decision.md`
- `careerhub/Docs/CareerGraph_Repo_Structure_Proposal.md`
- `careerhub/Docs/CareerGraph_Core_Principles_v14.md`

**Decision:**
```
Graph Memory Core (private)
        |
        ↓
CareerGraph (open source product)
```

Core provides storage, events, runtime. Product provides domain model, UI, workflows.

---

## ADR-002: File Format - .gmem vs .cgraph

**ID:** ADR-002  
**Title:** File Format Separation - .gmem for Core, .cgraph deprecated  
**Status:** ACCEPTED  
**Implementation Status:** Deferred  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-core  
**Summary:** .gmem is generic storage format for Graph Memory Core. .cgraph domain-specific format should be deprecated to avoid conflation.
**Note:** .cgraph domain format implementation remains open. .gmem is generic Graph Memory Core format.  
**Source Documents:**
- `careerhub/Docs/Graph_Memory_Separation_Decision.md`
- `careerhub/Docs/Graph_Memory_Core_Separation_v2.md`
- `careerhub/Docs/CareerGraph_Core_Principles_v5.md`
- `careerhub/Docs/CareerGraph_Core_Principles_v14.md`

**Decision:**
- `.gmem` = Graph Memory Core storage format
- `.cgraph` → domain-specific or deprecated
- Core knows generic format, domains map to it

**Note:** .cgraph domain format implementation remains open. .gmem is generic Graph Memory Core format.

---

## ADR-003: Two-Level MCP Architecture

**ID:** ADR-003  
**Title:** Two-Level MCP Architecture  
**Status:** ACCEPTED  
**Implementation Status:** Partial  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-mcp  
**Summary:** MCP tools split into core layer (graph operations) and domain layer (application tools). Core tools generic, domain tools specific.  
**Source Documents:**
- `careerhub/Docs/Graph_Memory_Two_Level_MCP.md`
- `careerhub/Docs/CareerGraph_Core_Principles_v14.md`

**Decision:**
```
Graph Memory Tools (core)
        |
        ↓
Domain Tools (CareerGraph)
```

Core tools: graph query, create, update, snapshot  
Domain tools: career workflows, vacancy matching, etc.

---

## ADR-004: Graph Language Human-First Philosophy

**ID:** ADR-004  
**Title:** Graph Language Human-First Philosophy  
**Status:** ACCEPTED PRINCIPLE  
**Implementation Status:** Open  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-language  
**Summary:** Graph Language designed for human authorship first, machine processing second. Language should be readable and writable by humans.
**Note:** Graph Language principles accepted. Concrete grammar/compiler implementation deferred.  
**Source Documents:**
- `careerhub/Docs/Graph_Language_Philosophy_Decision.md`
- `careerhub/Docs/Graph_Language_Model_Decision.md`
- `careerhub/Docs/Graph_Language_Decisions_v2.md`

**Decision:**
- Language syntax optimized for human readability
- Compiler handles optimization
- Domain experts can write directly
- Machine-readable but human-first

---

## ADR-005: Event Sourcing Model

**ID:** ADR-005  
**Title:** Event Sourcing Model for Graph Memory  
**Status:** ACCEPTED  
**Implementation Status:** Defined  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-core  
**Summary:** Graph is projection from event stream, not direct database. Events are source of truth.  
**Source Documents:**
- `careerhub/Docs/Graph_Memory_Architecture_Decision.md`
- `careerhub/Docs/Graph_Memory_Separation_Decision.md`
- `careerhub/Docs/CareerGraph_Repo_Structure_Proposal.md`

**Decision:**
```
Event Stream
      ↓
Graph Projection
      ↓
Current State
```

Events: SkillCreated, ProjectCreated, EvidenceAdded, DecisionRecorded, RelationshipCreated

Graph is projection, not persistence.

---

## ADR-006: Portability Requirements

**ID:** ADR-006  
**Title:** File Portability Between Installations  
**Status:** ACCEPTED  
**Implementation Status:** Partial  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-core  
**Summary:** Graph files must be portable between CareerGraph installations. File format self-contained.  
**Source Documents:**
- `careerhub/Docs/Graph_Memory_Portability_Decision.md`
- `careerhub/Docs/CareerGraph_Core_Principles_v6.md`

**Decision:**
- .gmem files portable
- Schema embedded in file
- No external dependencies
- Can migrate between installations

---

## ADR-007: Human Context Layer

**ID:** ADR-007  
**Title:** Human Context Layer Separation  
**Status:** ACCEPTED  
**Implementation Status:** Defined  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-core  
**Summary:** Fact Layer separate from Human Context Layer. Facts are objective, context is subjective interpretation.  
**Source Documents:**
- `careerhub/Docs/CareerGraph_Core_Principles_v14.md`
- `careerhub/Docs/CareerGraph_Core_Principles_v8.md`

**Decision:**
```
Facts: Project, Technology, Skill
Context: migration difficulty, leadership growth, career moments
```

Facts layer = structured data  
Human Context layer = interpretations, notes, reflections

---

## ADR-008: Agent Permission Model

**ID:** ADR-008  
**Title:** Agent as Entity with Permissions  
**Status:** ACCEPTED  
**Implementation Status:** Defined  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-mcp  
**Summary:** Agents defined as entities with read/propose/execute permissions. Agent execution via MCP to external AI model.  
**Source Documents:**
- `careerhub/Docs/CareerGraph_Core_Principles_v14.md`
- `careerhub/Docs/Graph_Memory_Two_Level_MCP.md`

**Decision:**
- Agent = Entity with permissions
- Permissions: read/propose/execute
- Execution via MCP to external AI
- Agent actions audited

---

## ADR-009: Graph Commit Model

**ID:** ADR-009  
**Title:** Graph Commit / Snapshot Checkpoints  
**Status:** ACCEPTED PRINCIPLE  
**Implementation Status:** Open  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-core  
**Summary:** Graph supports commit-based history similar to Git. Snapshots enable diff and evolution tracking.
**Note:** Event, Commit and Snapshot concepts accepted. Concrete serialization/diff algorithms deferred.  
**Source Documents:**
- `careerhub/Docs/Graph_Memory_Architecture_Decision.md`
- `careerhub/Docs/CareerGraph_Core_Principles_v14.md`

**Decision:**
- Graph Commit = snapshot checkpoint
- Enables graph diff
- Tracks evolution
- Career evolution visible

---

## ADR-010: Rules vs Workflows Separation

**ID:** ADR-010  
**Title:** Rules vs Workflows Separation  
**Status:** ACCEPTED  
**Implementation Status:** Defined  
**Date:** 2026-08-20  
**Owner Repository:** graph-memory-core  
**Summary:** Rules are reactive (event → state change). Workflows are orchestration (sequence of actions). Separate engines.  
**Source Documents:**
- `careerhub/Docs/CareerGraph_Core_Principles_v14.md`

**Decision:**
- Rules engine: reactive
- Workflows engine: orchestration
- Separate concerns

---

## ADR-011: Repo Structure Proposal

**ID:** ADR-011  
**Title:** Repository Structure Proposal  
**Status:** ACCEPTED  
**Implementation Status:** Defined  
**Date:** 2026-08-20  
**Owner Repository:** careerhub  
**Summary:** Ecosystem split into core, language, MCP, CLI, spec, and product repos.  
**Source Documents:**
- `careerhub/Docs/CareerGraph_Repo_Structure_Proposal.md`

**Decision:**
- graph-memory-core: engine
- graph-memory-language: compiler
- graph-memory-mcp: integration
- graph-memory-cli: tooling
- graph-memory-spec: public specs
- careerhub: product

---

## Registry Notes

### Decision Status Definitions
- **ACCEPTED:** Decision made and implemented
- **ACCEPTED PRINCIPLE:** Architectural principle accepted, implementation open
- **DEPRECATED:** Decision superseded
- **HYPOTHESIS:** Under consideration
- **WONTFIX:** Deliberately not pursued

### Implementation Status Definitions
- **Defined:** Implementation specification complete
- **Partial:** Implementation specification partially defined
- **Deferred:** Implementation deferred for later phase
- **Open:** Implementation not started

### Ownership
All decisions in this registry are owned by respective repositories. Updates must be coordinated with owners.

### Source Document Policy
Source documents remain in original location. This registry provides index, not duplication.

### Review Cycle
Registry reviewed quarterly or after major architectural changes.

---

**Registry Maintainer:** Architecture Team  
**Last Updated:** 2026-08-20  
**Version:** 1.0
