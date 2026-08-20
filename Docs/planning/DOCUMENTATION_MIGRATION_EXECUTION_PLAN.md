# DOCUMENTATION_MIGRATION_EXECUTION_PLAN.md

## Migration Overview

**Current State**

Documentation is currently scattered across `careerhub/Docs/` with mixed ownership: Core engine architecture, Language design, MCP protocol, and CareerHub product documents all coexist in the same directory.

**Migration Goal**

Separate documentation ownership by layer:
- **graph-memory-core**: Private Graph Memory Core engine infrastructure
- **graph-memory-language**: Human-first Graph Language layer
- **graph-memory-mcp**: MCP integration layer
- **graph-memory-spec**: Specification and decision registry
- **careerhub**: Product/Application layer only (CareerHub domain)

**Status**: Phases 1-3 completed as audit/migration planning. Physical file migration not yet executed.

---

## Migration Phases

### Phase 1: graph-memory-spec

**Status**: Completed

**Scope**: Decision registry and ADR validation

- Audit documentation ownership
- Establish decision registry
- Validate ADR references
- Create documentation migration plan

**Output** (all under `Docs/`):
- `ADR_VALIDATION_REPORT.md`
- `DECISION_REGISTRY.md`
- `DOCUMENTATION_MIGRATION_PLAN.md`
- `planning/MIGRATION_REPORT.md`
- `planning/DOCUMENTATION_MIGRATION_EXECUTION_PLAN.md` (this document)

---

### Phase 2A: graph-memory-core

**Status**: Completed

**Scope**: Create documentation structure for private Graph Memory Core engine

- **Source**: `careerhub/Docs/` (Core-owned ADRs)
- **Target**: `graph-memory-core/Docs/`

**Created Structure**:
```
Docs/
├── Architecture/
│   ├── CORE_ARCHITECTURE.md
│   └── RUNTIME_MODEL.md
├── Events/
│   └── EVENT_SOURCING_MODEL.md
├── Storage/
│   └── GMEM_STORAGE_MODEL.md
├── Snapshots/
│   └── SNAPSHOT_AND_COMMIT_MODEL.md
├── Provenance/
│   └── DATA_PROVENANCE.md
├── Queries/
│   └── GRAPH_QUERY_MODEL.md
└── MIGRATION_REPORT.md
```

**ADRs Referenced**: ADR-001, ADR-005, ADR-006, ADR-007, ADR-009, ADR-010

---

### Phase 2B: graph-memory-mcp

**Status**: Completed

**Scope**: Create documentation structure for MCP integration layer

- **Source**: `careerhub/Docs/` (Two-Level MCP Architecture)
- **Target**: `graph-memory-mcp/Docs/`

**Created Structure**:
```
Docs/
├── Protocol/
│   └── MCP_ARCHITECTURE.md
├── Tools/
│   └── TOOL_MODEL.md
├── Security/
│   └── PERMISSION_MODEL.md
├── Agents/
│   └── AGENT_INTEGRATION.md
└── MIGRATION_REPORT.md
```

**ADRs Referenced**: ADR-003, ADR-008

---

### Phase 2C: graph-memory-language

**Status**: Completed

**Scope**: Create documentation structure for Graph Language layer

- **Source**: `careerhub/Docs/` (Graph Language decisions)
- **Target**: `graph-memory-language/Docs/`

**Created Structure**:
```
Docs/
├── Philosophy/
│   └── LANGUAGE_PHILOSOPHY.md
├── Syntax/
│   └── LANGUAGE_CONCEPTS.md
├── Types/
│   └── TYPE_SYSTEM_MODEL.md
├── Compiler/
│   └── COMPILER_ARCHITECTURE.md
└── MIGRATION_REPORT.md
```

**ADRs Referenced**: ADR-004

---

### Phase 3: careerhub

**Status**: Audit completed

**Scope**: Audit CareerHub documentation to retain only Product/Application layer

- **Source**: `careerhub/Docs/`
- **Target**: Documentation map created — no files moved yet

**Created**:
- `careerhub/Docs/CAREERHUB_DOCUMENTATION_MAP.md`

**Categorization**:
- **KEEP**: Product vision, domain model, user journey, MVP scope, product decisions
- **MOVE**: Core engine, Language, MCP docs → respective repositories
- **ARCHIVE**: Historical versions (Core_Principles v1-v14)

**Constraints**:
- CareerHub retains: Product vision, MVP scope, User journey, Career domain model, Vacancy model, Application tracking, Matching logic, UI/Product decisions, User experience
- CareerHub excludes: Core engine architecture, Event sourcing implementation, .gmem format, MCP protocol, Language/compiler design

---

## Remaining Actions

### 1. Physical File Migration

**Action Required**: Move categorized documents from `careerhub/Docs/` to target repositories based on CAREERHUB_DOCUMENTATION_MAP.md categorization.

**Priority**: High

**Details**:
- Move documents categorized as **MOVE** to respective `graph-memory-*` repositories
- Maintain directory structure in target repositories
- Preserve file timestamps and metadata

---

### 2. Archive Old Docs

**Action Required**: Archive historical versions and superseded documents.

**Priority**: Medium

**Details**:
- Move `CareerGraph_Core_Principles_v1.md` through `v14.md` to `careerhub/Docs/archive/`
- Move outdated engineering standards and repo structure proposals to archive
- Keep only latest version of each document in active directory

---

### 3. Update References

**Action Required**: Update cross-references between documents after migration.

**Priority**: High

**Details**:
- Update internal links in migrated documents to point to new locations
- Update ADR references to use canonical repository paths
- Replace direct file paths with repository references
- Verify Decision Registry references are accurate

---

### 4. Create README Links

**Action Required**: Create README files in each repository with documentation navigation links.

**Priority**: Medium

**Details**:
- Create `graph-memory-core/Docs/README.md` with links to Architecture, Events, Storage, etc.
- Create `graph-memory-mcp/Docs/README.md` with links to Protocol, Tools, Security, Agents
- Create `graph-memory-language/Docs/README.md` with links to Philosophy, Syntax, Types, Compiler
- Create `careerhub/Docs/README.md` with links to Product-only documents

---

### 5. Verify Cross-Repository References

**Action Required**: Verify all cross-repository references are valid after migration.

**Priority**: High

**Details**:
- Check that ADR references in migrated docs point to correct repositories
- Verify references between Core/Language/MCP layers are accurate
- Validate that CareerHub documents don't reference migrated infrastructure docs
- Check for broken links and orphaned references

---

## Migration Rules

### 1. No Duplicated Source of Truth

- Each document has a single canonical location
- No copies of documents across repositories
- References instead of duplication
- ADR documents remain in canonical repository

### 2. References Instead of Copies

- Use cross-repository references to documents rather than copying content
- Use relative paths and repository names for references
- Maintain a single source of truth for each document
- Update links when documents move

### 3. ADRs Remain Immutable

- ADRs are immutable once accepted
- Never modify accepted ADRs for migration purposes
- If clarification needed, create new ADR or amendment
- Historical ADR versions preserved in archive

### 4. Historical Docs Preserved

- All documents retained in archive before removal from active directory
- Archive directory structure mirrors active directory
- Document removal from active directory requires archive preservation
- No document deletion without archiving

### 5. Documentation Layer Boundaries

- **Core**: Private engine infrastructure, no domain concepts
- **Language**: Human-first interface, no implementation details
- **MCP**: Integration layer, no domain workflows
- **CareerHub**: Product/Application layer only
- No mixing of layer concerns in documentation

### 6. No New Architectural Decisions

- This plan documents migration only
- No new architectural decisions should be made during migration
- Focus on categorization and movement, not design changes
- Any architectural questions deferred to appropriate repository owners

---

## Migration Timeline

**Completed**:
- Phase 1: graph-memory-spec audit/migration
- Phase 2A: graph-memory-core documentation creation
- Phase 2B: graph-memory-mcp documentation creation
- Phase 2C: graph-memory-language documentation creation
- Phase 3: careerhub documentation audit

**Pending**:
- Physical file migration (Remaining Actions 1)
- Archive historical docs (Remaining Actions 2)
- Update references (Remaining Actions 3)
- Create README links (Remaining Actions 4)
- Verify cross-repository references (Remaining Actions 5)

---

## Success Criteria

1. **Separation of Concerns**: Each repository contains only documentation relevant to its layer
2. **No Duplication**: Single source of truth for each document
3. **Preservation**: All historical documents archived, none deleted
4. **Cross-Repository References**: Valid links between repositories where layers interact
5. **CareerHub Purity**: CareerHub contains only product/application documentation
6. **ADR Integrity**: ADRs remain immutable and properly referenced

---

## Ownership

**Current Owner**: Documentation Migration Initiative

**Repository Owners**:
- **graph-memory-core**: Core Engine Team
- **graph-memory-language**: Language Team
- **graph-memory-mcp**: MCP Integration Team
- **graph-memory-spec**: Specification Team
- **careerhub**: Product Team

**Next Steps**: Assign migration execution to repository owners with defined timelines for Remaining Actions.
