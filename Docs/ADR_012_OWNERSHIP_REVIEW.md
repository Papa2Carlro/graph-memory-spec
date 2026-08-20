# ADR-012 Ownership Review

**Date:** 2026-08-20
**Document:** `Docs/ADRs/ADR-012_Schema_Architecture_Decision.md`
**Source:** `careerhub/Docs/CareerGraph_Schema_Architecture_Decision.md`

## Ownership Analysis

Document describes both:

### Generic Graph Memory Schema Architecture

- Core is domain-agnostic
- Core has schema engine
- Core owns Entity Types, fields, Relations, Events, validation, indexes
- Core is schema-agnostic, schema engine validates structure
- Portability: swap domain schema without touching Core
- Extensibility: DocHub, other domains reuse Core with own schema

### CareerHub Domain Schema

- Explicit examples from CareerGraph domain:
  - Entity: Person, Skill, Project, Experience, Vacancy, Application, Interview, Company
  - Relations: WORKED_ON, HAS_SKILL, MATCHES, APPLIED_TO
  - File: `career.schema`
- Document uses CareerGraph as primary illustration

## Classification

**Mixed ownership: A + B**

- Generic schema architecture principles are spec-owned
- CareerGraph domain entities/relations are product-owned

## Recommendation

Keep document in `graph-memory-spec` **only if** it is refactored to remove CareerGraph-specific examples and retain only generic schema architecture. Current version contains product-specific domain examples that belong to CareerHub.

**Current state:** Document is **B-weighted** with domain-specific CareerGraph schema. The principles section is generic, but the concrete examples are CareerGraph-specific.

**Decision:** Document should remain in `careerhub/Docs/` as product decision, or be split:

- Generic schema architecture → `graph-memory-spec/Docs/ADRs/`
- CareerGraph domain schema → `careerhub/Docs/`

## Compliance

- Content not modified per request
- Ownership determined: Mixed, primarily domain-specific (B)
- No new architectural decisions created
