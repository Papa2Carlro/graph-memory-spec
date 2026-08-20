# Documentation Migration Plan

**Version:** 1.0  
**Date:** 2026-08-20  
**Status:** Planning

## Purpose

Plan for migrating documentation from careerhub/Docs/ to appropriate repositories based on DECISION_REGISTRY.md and DOCUMENTATION_OWNERSHIP_MAP.md.

Decision registry has been created. This migration plan maps all 38 inventoried documents to target repositories.

---

## Migration Principles

1. **Single source of truth** — documents live in one repo, referenced elsewhere
2. **Domain ownership** — each repo owns docs for its domain
3. **Legacy preservation** — historical versions archived, not deleted
4. **Archive vs Active** — documents with status OUTDATED move to archive/

---

## Migration Matrix

### ADRs → graph-memory-spec

| Current Location | Target | Migration Action | Dependencies |
|---|---|---|---|
| `careerhub/Docs/Graph_Memory_Architecture_Decision.md` | `graph-memory-spec/Docs/ADRs/ADR-001.md` | Move and rename | ADR-001 |
| `careerhub/Docs/Graph_Memory_Separation_Decision.md` | `graph-memory-spec/Docs/ADRs/ADR-002.md` | Move and rename | ADR-002 |
| `careerhub/Docs/Graph_Memory_Core_Separation_v2.md` | `graph-memory-spec/Docs/ADRs/` | Archive to archive/ | ADR-002 |
| `careerhub/Docs/Graph_Memory_Portability_Decision.md` | `graph-memory-spec/Docs/ADRs/ADR-006.md` | Move and rename | ADR-006 |
| `careerhub/Docs/Graph_Memory_Two_Level_MCP.md` | `graph-memory-spec/Docs/ADRs/ADR-003.md` | Move and rename | ADR-003 |
| `careerhub/Docs/Graph_Language_Philosophy_Decision.md` | `graph-memory-spec/Docs/ADRs/ADR-004.md` | Move and rename | ADR-004 |
| `careerhub/Docs/Graph_Language_Model_Decision.md` | `graph-memory-spec/Docs/ADRs/` | Archive to archive/ | ADR-004 |
| `careerhub/Docs/Graph_Language_Decisions_v2.md` | `graph-memory-spec/Docs/ADRs/` | Archive to archive/ | ADR-004 |
| `careerhub/Docs/Graph_Language_Syntax_Rules_Decision.md` | `graph-memory-spec/Docs/ADRs/` | Archive to archive/ | ADR-004 |
| `careerhub/Docs/Graph_Runtime_Markup_Language_Decision.md` | `graph-memory-spec/Docs/ADRs/` | Archive to archive/ | ADR-004 |
| `careerhub/Docs/Graph_Layers_Compiler_Browser_Decision.md` | `graph-memory-spec/Docs/ADRs/` | Archive to archive/ | ADR-004 |

**Rationale:** ADRs belong in spec repository as public architectural records.

---

### Language Design → graph-memory-language

| Current Location | Target | Migration Action | Dependencies |
|---|---|---|---|
| `careerhub/Docs/Graph_Language_Philosophy_Decision.md` | `graph-memory-language/Docs/LANGUAGE_PHILOSOPHY.md` | Copy and reference | ADR-004 |
| `careerhub/Docs/Graph_Language_Model_Decision.md` | `graph-memory-language/Docs/LANGUAGE_MODEL.md` | Copy and reference | ADR-004 |
| `careerhub/Docs/Graph_Language_Decisions_v2.md` | `graph-memory-language/Docs/` | Copy relevant | ADR-004 |
| `careerhub/Docs/Graph_Language_Syntax_Rules_Decision.md` | `graph-memory-language/Docs/SYNTAX.md` | Copy and reference | ADR-004 |
| `careerhub/Docs/Graph_Layers_Compiler_Browser_Decision.md` | `graph-memory-language/Docs/COMPILER_ARCH.md` | Move | ADR-004 |

**Rationale:** Graph Language design documents belong in language repo.

---

### Core Architecture → graph-memory-core

| Current Location | Target | Migration Action | Dependencies |
|---|---|---|---|
| `careerhub/Docs/Graph_Memory_Architecture_Decision.md` | `graph-memory-core/Docs/ARCHITECTURE.md` | Copy and reference | ADR-001 |
| `careerhub/Docs/Graph_Memory_Separation_Decision.md` | `graph-memory-core/Docs/SEPARATION.md` | Copy and reference | ADR-002 |
| `careerhub/Docs/Graph_Memory_Core_Separation_v2.md` | `graph-memory-core/Docs/SEPARATION.md` | Merge | ADR-002 |
| `careerhub/Docs/Graph_Memory_Portability_Decision.md` | `graph-memory-core/Docs/PORTABILITY.md` | Copy and reference | ADR-006 |
| `careerhub/Docs/CareerGraph_Core_Principles_v14.md` | `graph-memory-core/Docs/CORE_PRINCIPLES.md` | Reference only | ADR-001, ADR-005 |
| `careerhub/Docs/CareerGraph_Core_Decisions.md` | `graph-memory-core/Docs/DECISIONS.md` | Copy relevant | Multiple ADRs |

**Rationale:** Core architecture documents belong in core repo.

---

### MCP Design → graph-memory-mcp

| Current Location | Target | Migration Action | Dependencies |
|---|---|---|---|
| `careerhub/Docs/Graph_Memory_Two_Level_MCP.md` | `graph-memory-mcp/Docs/TWO_LEVEL_ARCH.md` | Move | ADR-003 |
| `careerhub/Docs/CareerGraph_Core_Principles_v14.md` | `graph-memory-mcp/Docs/AGENT_MODEL.md` | Reference Agent section | ADR-008 |

**Rationale:** MCP architecture documents belong in MCP repo.

---

### CLI → graph-memory-cli

| Current Location | Target | Migration Action | Dependencies |
|---|---|---|---|
| `careerhub/Docs/CareerGraph_Engineering_Standards.md` | `graph-memory-cli/Docs/CLI_STANDARDS.md` | Copy relevant | Standards |
| `careerhub/Docs/standards/` | `graph-memory-cli/Docs/STANDARDS/` | Copy relevant | Standards |

**Rationale:** CLI-specific standards and documentation.

---

### Product Documentation → careerhub

| Current Location | Target | Migration Action | Dependencies |
|---|---|---|---|
| `careerhub/Docs/CareerGraph_Core_Principles_v14.md` | `careerhub/Docs/PRODUCT_PRINCIPLES.md` | Keep product-specific sections | ADR-001 |
| `careerhub/Docs/CareerGraph_Product_Documentation.md` | `careerhub/Docs/PRODUCT_DOCS.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_Product_System_Model.md` | `careerhub/Docs/SYSTEM_MODEL.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_MVP_Vision.md` | `careerhub/Docs/MVP_VISION.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_MVP_Direction_Decisions.md` | `careerhub/Docs/MVP_DECISIONS.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_User_Journey.md` | `careerhub/Docs/USER_JOURNEY.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_Domain_Model.md` | `careerhub/Docs/DOMAIN_MODEL.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_Graph_Model_Decisions.md` | `careerhub/Docs/GRAPH_MODEL.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_Schema_Architecture_Decision.md` | `careerhub/Docs/SCHEMA_ARCH.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_Repo_Structure_Proposal.md` | `careerhub/Docs/ARCHITECTURE.md` | Keep as-is | Product |
| `careerhub/Docs/CareerGraph_Core_Decisions.md` | `careerhub/Docs/CORE_DECISIONS.md` | Keep as-is | Product |

**Rationale:** Product documentation remains in careerhub.

---

### Standards → All Repos

| Current Location | Target | Migration Action | Dependencies |
|---|---|---|---|
| `careerhub/Docs/standards/UI_DESIGN_SYSTEM_STANDARD.md` | `careerhub/Docs/standards/UI_DESIGN_SYSTEM_STANDARD.md` | Keep | Product |
| `careerhub/Docs/standards/backend/*.md` | Distribute to appropriate repos | Move relevant | Standards |
| `careerhub/Docs/standards/frontend/*.md` | `careerhub/` | Keep | Product |

**Rationale:** Standards distributed based on domain.

---

## Historical Versions → Archive

| Document Series | Action | Location |
|---|---|---|
| `CareerGraph_Core_Principles_v1.md` through `v13.md` | Archive | `careerhub/Docs/archive/principles/` |
| `CareerGraph_Codebase_Analysis.md` | Archive | `careerhub/Docs/archive/analysis/` |

**Rationale:** Historical versions preserved for reference but not in active docs.

---

## Migration Steps

### Phase 1: Spec Repository
1. Create ADRs folder structure in `graph-memory-spec/Docs/ADRs/`
2. Migrate core ADRs
3. Update DECISION_REGISTRY.md with file paths
4. Push to `graph-memory-spec`

### Phase 2: Core Repository
1. Create architecture docs in `graph-memory-core/Docs/`
2. Migrate architecture documents
3. Link to ADRs
4. Push to `graph-memory-core`

### Phase 3: Language Repository
1. Migrate language design docs
2. Update references
3. Push to `graph-memory-language`

### Phase 4: MCP Repository
1. Migrate MCP architecture docs
2. Update references
3. Push to `graph-memory-mcp`

### Phase 5: CareerHub Cleanup
1. Move historical versions to archive
2. Update remaining product docs
3. Remove migrated files or keep references
4. Commit cleanup

---

## Dependency Matrix

```
DECISION_REGISTRY.md
        ↓
DOCUMENTATION_OWNERSHIP_MAP.md
        ↓
DOCUMENTATION_MIGRATION_PLAN.md
        ↓
ADRs in graph-memory-spec
        ↓
Arch docs in graph-memory-core/language/mcp
        ↓
Product docs in careerhub
```

---

## Risks

1. **Link rot** — Documents reference each other, migration must update paths
2. **Historical loss** — Archive must preserve all versions
3. **Concurrent editing** — Lock documents during migration
4. **Ownership confusion** — Clear ownership before migration

---

## Acceptance Criteria

- [ ] All ADRs migrated to graph-memory-spec
- [ ] DECISION_REGISTRY.md complete with 11 ADRs
- [ ] graph-memory-core has architecture docs
- [ ] graph-memory-language has language docs
- [ ] graph-memory-mcp has MCP docs
- [ ] careerhub has product docs only
- [ ] Historical versions archived
- [ ] Cross-references updated
- [ ] All repos pushed to GitHub

---

**Migration Owner:** Architecture Team  
**Last Updated:** 2026-08-20  
**Version:** 1.0
