# GMEM_FORMAT.md Split Report

**Date:** 2026-08-20  
**Owner:** graph-memory-spec  
**Auditor:** spec-ownership-audit

## Summary

`GMEM_FORMAT.md` contained mixed ownership: generic `.gmem` format specification + CareerHub domain examples (SkillCreated, Project/Technology/Skill). This report documents the split.

## Problem

| Issue | Details |
|---|---|
| Mixed ownership | Generic format concepts and CareerHub domain examples co-located |
| Source of truth violation | Spec should contain only generic concepts |
| Domain leakage | SkillCreated, Project/Technology/Skill examples belong to careerhub |

## Split Strategy

| Original Section | Destination | Reason |
|---|---|---|
| Purpose, Design Principles, High-Level Structure, Header, Schema, Event Stream generic, Commits, Context Layer generic, Portability, Versioning/Compatibility, Relationship to Other Formats | `graph-memory-spec/Docs/Formats/GMEM_FORMAT_OVERVIEW.md` | Generic format specification, spec-owned |
| Event Stream examples: SkillCreated, ProjectCreated, EvidenceAdded, DecisionRecorded, RelationshipCreated | `careerhub/Docs/Architecture/CAREER_GRAPH_FORMAT_EXAMPLE.md` | Domain examples, careerhub-owned |
| Fact vs Context with Project/Technology/Skill examples | `careerhub/Docs/Architecture/CAREER_GRAPH_FORMAT_EXAMPLE.md` | Domain-specific illustration |
| Schema example with Person/Project/Technology/Skill | `careerhub/Docs/Architecture/CAREER_GRAPH_FORMAT_EXAMPLE.md` | Domain schema mapping |

## Files Created

1. `graph-memory-spec/Docs/Formats/GMEM_FORMAT_OVERVIEW.md`
   - Purpose, Design Principles, Structure
   - Generic events: EntityCreated, EntityUpdated, RelationshipCreated
   - Versioning concepts, Compatibility principles
   - No domain examples

2. `careerhub/Docs/Architecture/CAREER_GRAPH_FORMAT_EXAMPLE.md`
   - Domain Mapping: Person, Project, Technology, Skill, Evidence, Decision
   - Domain-specific event examples
   - Fact vs Context with CareerGraph examples
   - Schema definition example for CareerGraph

## Files Deprecated

- `graph-memory-spec/Docs/Formats/GMEM_FORMAT.md` — **Mixed ownership, superseded by split**

  **Action:** Keep for historical reference, but source of truth is now split.

## Ownership Boundaries

| Repository | Content | Source of Truth |
|---|---|---|
| `graph-memory-spec` | `.gmem` format specification, generic principles | Yes |
| `careerhub` | CareerGraph mapping, domain examples | Yes |

## Validation

- No new architectural decisions added
- No duplication of detailed documentation
- Only navigation and ownership clarification
- Generic concepts preserved in spec
- Domain examples moved to careerhub

## References

- `Docs/SPEC_OWNERSHIP_AUDIT_REPORT.md`
- `graph-memory-spec/Docs/Formats/GMEM_FORMAT_OVERVIEW.md`
- `careerhub/Docs/Architecture/CAREER_GRAPH_FORMAT_EXAMPLE.md`
