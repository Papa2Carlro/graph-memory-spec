# ADR-012 Split Report

**Date:** 2026-08-20
**Source Document:** `ADR-012_Schema_Architecture_Decision.md`

## Split Overview

Original ADR-012 contained mixed ownership content:
- Generic Graph Memory schema architecture principles
- CareerHub domain schema examples

Split into two documents preserving ownership boundaries.

## Split Table

| Original Section | Destination | Reason |
|------------------|-------------|--------|
| Graph Memory Core — schema engine concept | `graph-memory-spec/Docs/ADRs/ADR-012-Graph-Schema-Architecture.md` | Generic Core schema architecture, spec-owned |
| Example EntityType generic structure | `graph-memory-spec/Docs/ADRs/ADR-012-Graph-Schema-Architecture.md` | Generic schema concepts, spec-owned |
| Domain Schema — career.schema introduction | `careerhub/Docs/Decisions/Career-Schema-Architecture.md` | CareerGraph domain-specific, product-owned |
| Entities: Person, Skill, Project, Experience, Vacancy, Application, Interview, Company | `careerhub/Docs/Decisions/Career-Schema-Architecture.md` | Career domain entities, product-owned |
| Relations: WORKED_ON, HAS_SKILL, MATCHES, APPLIED_TO | `careerhub/Docs/Decisions/Career-Schema-Architecture.md` | Career domain relations, product-owned |
| Composition diagram Core + Career Schema = CareerGraph | Both documents reference | Conceptual relationship retained |
| Extensibility example DocHub | `graph-memory-spec/Docs/ADRs/ADR-012-Graph-Schema-Architecture.md` | Generic extensibility, spec-owned |
| Principles: Core schema-agnostic, domain schemas separate | `graph-memory-spec/Docs/ADRs/ADR-012-Graph-Schema-Architecture.md` | Generic principles, spec-owned |
| Principles: Domain provides semantics | `careerhub/Docs/Decisions/Career-Schema-Architecture.md` | Domain semantics, product-owned |
| Principles: Portability and Extensibility | `graph-memory-spec/Docs/ADRs/ADR-012-Graph-Schema-Architecture.md` | Generic portability, spec-owned |

## Documents Created

### Spec-owned
- `graph-memory-spec/Docs/ADRs/ADR-012-Graph-Schema-Architecture.md`
  - Generic schema concepts
  - Entities, relations, schema evolution, validation principles
  - No CareerHub domain examples

### Product-owned
- `careerhub/Docs/Decisions/Career-Schema-Architecture.md`
  - Career domain entities
  - career.schema
  - Product relationships

## Original Document

ADR-012_Schema_Architecture_Decision.md preserved unchanged for history.

## Constraints

- ✅ No architectural decisions changed
- ✅ No content modified, only separated
- ✅ Ownership boundaries respected
- ✅ Original document retained
