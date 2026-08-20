# Phase 4A Physical Migration Report

**Date:** 2026-08-20
**Phase:** 4A — Physical migration of spec-owned documentation from careerhub

## Goal

Migrate specification-owned documentation from `careerhub/Docs/` to `graph-memory-spec/Docs/`.
Keep product docs in careerhub. No architectural decisions are changed.

## Migration Table

| Source | Destination | Action | Reason |
|--------|-------------|--------|--------|
| `careerhub/Docs/CareerGraph_Schema_Architecture_Decision.md` | `graph-memory-spec/Docs/ADRs/ADR-012_Schema_Architecture_Decision.md` | MOVE AS REFERENCE | Schema architecture decisions belong to spec layer. Document is spec-owned, not product-owned. |

## Classification Summary

### Spec-owned (Migrated)

- `CareerGraph_Schema_Architecture_Decision.md` → `graph-memory-spec/Docs/ADRs/ADR-012_Schema_Architecture_Decision.md`

### Keep As Current Doc (Product layer)

- CareerGraph_MVP_Vision.md
- CareerGraph_User_Journey.md
- CareerGraph_Domain_Model.md
- CareerGraph_MVP_Direction_Decisions.md
- CareerGraph_Product_Documentation.md
- CareerGraph_Product_System_Model.md
- CareerGraph_Core_Decisions.md
- CareerGraph_Graph_Model_Decisions.md
- CareerGraph_Architecture_Principles.md
- CareerGraph_Codebase_Analysis.md

### Move As Reference (Infrastructure layers)

- Graph_Memory_Architecture_Decision.md → graph-memory-core
- Graph_Memory_Separation_Decision.md → graph-memory-core
- Graph_Memory_Core_Separation_v2.md → graph-memory-core
- Graph_Memory_Portability_Decision.md → graph-memory-core
- Graph_Language_Philosophy_Decision.md → graph-memory-language
- Graph_Language_Model_Decision.md → graph-memory-language
- Graph_Language_Syntax_Rules_Decision.md → graph-memory-language
- Graph_Language_Decisions_v2.md → graph-memory-language
- Graph_Runtime_Markup_Language_Decision.md → graph-memory-language
- Graph_Layers_Compiler_Browser_Decision.md → graph-memory-language
- Graph_Memory_Two_Level_MCP.md → graph-memory-mcp

### Archive

- CareerGraph_Core_Principles_v1.md … v14.md — historical versions
- CareerGraph_Engineering_Standards.md — implementation details
- CareerGraph_Repo_Structure_Proposal.md — superseded

## Changes Applied

- Copied spec-owned document to `graph-memory-spec/Docs/ADRs/ADR-012_Schema_Architecture_Decision.md`
- Updated `graph-memory-spec/Docs/README.md` Documentation Map to include ADR-012
- No content modifications made; document preserved as-is
- No duplicate copies created; original remains in careerhub for reference until deprecation plan

## Constraints

- ✅ No new architectural decisions created
- ✅ No duplicates
- ✅ No historical documents deleted
- ✅ No architectural content modified
- ✅ Internal references updated in Docs/README.md

## Next Steps

- Phase 4B: Migrate core/language/mcp owned docs
- Update DECISION_REGISTRY.md to reference ADR-012
- Deprecate original file in careerhub with pointer to new location
