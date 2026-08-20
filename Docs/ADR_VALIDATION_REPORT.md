# ADR Validation Report

**Date:** 2026-08-20  
**Scope:** Validation of 11 architectural decisions (ADR-001 through ADR-011)  
**Purpose:** Identify decisions with implementation questions requiring follow-up

---

## ADR-001: Core vs Product Separation

| Question | Answer |
|---|---|
| **Decision fully defined?** | ✅ Yes — Clear separation: Core = generic engine, Product = open source application |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — defines ownership and boundaries |
| **Status recommendation** | **ACCEPTED** — no changes needed |
| **Implementation questions** | None identified. Boundary between core and product is well-established in v14 and all source documents. |

---

## ADR-002: File Format - .gmem vs .cgraph

| Question | Answer |
|---|---|
| **Decision fully defined?** | ⚠️ Partially — Format separation declared but implementation mapping needs work |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — format ownership |
| **Status recommendation** | **ACCEPTED** with implementation follow-up needed |
| **Implementation questions** | • Need mapping from existing `.cgraph` files to `.gmem`<br>• Deprecation plan for `.cgraph` in CareerGraph codebase<br>• Migration tooling requirements |

---

## ADR-003: Two-Level MCP Architecture

| Question | Answer |
|---|---|
| **Decision fully defined?** | ✅ Yes — Clear two-level split: core tools + domain tools |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — MCP layering |
| **Status recommendation** | **ACCEPTED** — good definition |
| **Implementation questions** | • Core tool signatures need finalization<br>• Domain tool examples (CareerGraph-specific)<br>• Testing strategy for boundary between layers |

---

## ADR-004: Graph Language Human-First Philosophy

| Question | Answer |
|---|---|
| **Decision fully defined?** | ⚠️ Partially — Philosophy clear but syntax decisions pending |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — human-first design stance |
| **Status recommendation** | **ACCEPTED PRINCIPLE / IMPLEMENTATION OPEN** |
| **Implementation questions** | • Concrete syntax grammar not defined<br>• Compiler pipeline stages not specified<br>• Domain example grammars needed<br>• Tooling (formatter, linter) requirements |

---

## ADR-005: Event Sourcing Model

| Question | Answer |
|---|---|
| **Decision fully defined?** | ✅ Yes — Event stream → Graph Projection → State is clear |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — event sourcing philosophy |
| **Status recommendation** | **ACCEPTED** — well-defined |
| **Implementation questions** | • Event schema definition needed<br>• Migration from existing data<br>• Query patterns for event stream |

---

## ADR-006: Portability Requirements

| Question | Answer |
|---|---|
| **Decision fully defined?** | ⚠️ Partially — Portability principle stated but format details sparse |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — portability requirement |
| **Status recommendation** | **ACCEPTED** |
| **Implementation questions** | • Embedded schema specification needed<br>• Versioning strategy for portable files<br>• Cross-installation compatibility tests |

---

## ADR-007: Human Context Layer Separation

| Question | Answer |
|---|---|
| **Decision fully defined?** | ✅ Yes — Facts vs Context separation clear |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — layering concern |
| **Status recommendation** | **ACCEPTED** — well-articulated |
| **Implementation questions** | • Fact schema definition<br>• Context metadata model<br>• Query separation patterns |

---

## ADR-008: Agent Permission Model

| Question | Answer |
|---|---|
| **Decision fully defined?** | ✅ Yes — read/propose/execute permissions defined |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — agent governance |
| **Status recommendation** | **ACCEPTED** — good definition |
| **Implementation questions** | • Permission enforcement mechanism<br>• Agent action auditing details<br>• MCP integration contract |

---

## ADR-009: Graph Commit / Snapshot Model

| Question | Answer |
|---|---|
| **Decision fully defined?** | ⚠️ Partially — Concept of commits/snapshots stated but diff mechanics pending |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — versioning approach |
| **Status recommendation** | **ACCEPTED PRINCIPLE / IMPLEMENTATION OPEN** |
| **Implementation questions** | • Commit/Snapshot format definition<br>• Diff/merge algorithm<br>• UI for viewing graph evolution<br>• Conflict resolution strategy |

---

## ADR-010: Rules vs Workflows Separation

| Question | Answer |
|---|---|
| **Decision fully defined?** | ✅ Yes — Reactive vs orchestration distinction clear |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — engine separation |
| **Status recommendation** | **ACCEPTED** — well-defined |
| **Implementation questions** | • Rules engine specification<br>• Workflow engine API<br>• Integration patterns |

---

## ADR-011: Repository Structure Proposal

| Question | Answer |
|---|---|
| **Decision fully defined?** | ✅ Yes — repo map clearly defined |
| **Architectural principle or implementation detail?** | ✅ Architectural principle — repo ownership |
| **Status recommendation** | **ACCEPTED** — complete |
| **Implementation questions** | • Repo creation and migration tasks<br>• Cross-repo reference patterns<br>• Package versioning strategy |

---

## Summary

### Fully Defined Decisions (ACCEPTED)
- ADR-001, ADR-005, ADR-007, ADR-008, ADR-011
- No implementation follow-up required at registry level

### Accepted with Implementation Open
- ADR-002, ADR-004, ADR-006, ADR-009
- Require concrete implementation specifications

### Accepted Principle / Implementation Open
- ADR-003, ADR-004 (duplicate entry), ADR-010
- Philosophy defined; implementation needs detail

### Recommended Status Changes
| ADR | Current | Recommended |
|---|---|---|
| ADR-002 | ACCEPTED | ACCEPTED (implementation follow-up) |
| ADR-004 | ACCEPTED | ACCEPTED PRINCIPLE / IMPLEMENTATION OPEN |
| ADR-009 | ACCEPTED | ACCEPTED PRINCIPLE / IMPLEMENTATION OPEN |

### Next Actions
1. **ADR-004**: Define concrete Graph Language syntax grammar
2. **ADR-002**: Create `.cgraph` → `.gmem` migration plan and tooling
3. **ADR-009**: Specify commit/snapshot format and diff algorithm
4. **ADR-003**: Finalize core MCP tool signatures
5. **ADR-006**: Define embedded schema format for .gmem portability

---

**Report Generated:** 2026-08-20  
**Validator:** Architecture Team  
**Next Review:** 2026-11-20 (quarterly)