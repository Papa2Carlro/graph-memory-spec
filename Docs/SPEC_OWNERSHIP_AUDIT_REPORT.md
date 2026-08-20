# SPEC Ownership Audit Report

**Date:** 2026-08-20
**Scope:** `graph-memory-spec/Docs/`
**Goal:** Find documents mixing Graph Memory generic concepts with CareerHub domain concepts

## Audit Methodology

Searched for domain-specific terms: career, CareerGraph, person, skill, vacancy, application, interview, company

## Findings

| Document | Issue | Ownership | Recommendation |
|----------|-------|-----------|----------------|
| `ADRs/ADR-001.md` | References CareerGraph, careerhub docs | Spec owns decision, references product docs | KEEP — references are valid; decision is generic |
| `ADRs/ADR-002.md` | References CareerGraph Core Principles | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-003.md` | References CareerGraph tools | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-004.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-005.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-006.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-007.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-008.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-009.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-010.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-011.md` | References CareerGraph | Spec owns decision, references product docs | KEEP — references are valid |
| `ADRs/ADR-012-Schema_Architecture_Decision.md` | Mixed generic + CareerGraph domain entities (Person, Skill, Project, Experience, Vacancy, Application, Interview, Company, career.schema) | Mixed | **SPLIT** — already split into ADR-012-Graph-Schema-Architecture.md (spec) and careerhub/Docs/Decisions/Career-Schema-Architecture.md (product). Original retained for history. |
| `ADRs/ADR-012-Graph-Schema-Architecture.md` | Contains generic schema only | Spec | KEEP |
| `GRAPH_MEMORY_OVERVIEW.md` | Mentions CareerGraph as example application layer, SkillCreated event, career evolution, Project/Technology/Skill as facts | Spec with examples | KEEP — overview legitimately references example product for illustration. Domain examples are illustrative, not prescriptive. Consider adding note that examples are illustrative. |
| `DECISION_REGISTRY.md` | References careerhub docs as sources, mentions CareerGraph | Spec registry | KEEP — registry indexes source documents; references are valid |
| `Formats/GMEM_FORMAT.md` | Mentions SkillCreated event, Project/Technology/Skill as facts, career moments | Spec format | **REVIEW** — format spec should be generic. Events like SkillCreated and facts like Project/Skill are domain examples. Format spec should use generic placeholders. Recommend genericize examples. |
| `README.md` | References CareerGraph | Spec navigation | KEEP — navigation references related repos |

## Classification Summary

### KEEP
- ADRs 001-011 — decisions are generic, references to careerhub are source provenance
- ADR-012-Graph-Schema-Architecture.md — generic only
- GRAPH_MEMORY_OVERVIEW.md — overview legitimately illustrates with examples
- DECISION_REGISTRY.md — registry indexing sources
- README.md — navigation

### SPLIT
- ADR-012_Schema_Architecture_Decision.md — already split; original preserved

### REVIEW / GENERICIZE
- Formats/GMEM_FORMAT.md — contains domain-specific examples (SkillCreated, Project/Technology/Skill). Format spec should be generic with placeholders. Recommend replace domain examples with generic ones.

### ARCHIVE
- None identified in current scope

## Recommendations

1. **Formats/GMEM_FORMAT.md** — Genericize domain examples. Replace SkillCreated with EventName. Replace Project/Technology/Skill with EntityType/Field examples. Keep structure generic.

2. **GRAPH_MEMORY_OVERVIEW.md** — Add explicit note that CareerGraph examples are illustrative, not normative.

3. **ADR References** — Current reference pattern to careerhub docs is acceptable as provenance. No changes needed.

## Constraints

- No files modified automatically per request
- No architectural decisions changed
- Ownership classification only
