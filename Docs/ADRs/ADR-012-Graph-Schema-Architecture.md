# ADR-012 Graph Schema Architecture

## Graph Memory Core
Core не знає доменів.

Він має **schema engine**.

Його задача:

- знати, що існують Entity Types;
- знати поля;
- знати Relations;
- знати Events;
- валідовувати структуру;
- будувати індекси.

Наприклад:

```
EntityType

{
  name: "<EntityName>",

  fields:
    - name
    - created_at
    - metadata

  relations:
    - <RELATION_NAME>
    - <RELATION_NAME>
}
```

Але Core не знає семантики Entity.

---

Тобто:

```
Graph Memory Core

        +
        
Domain Schema

        =

Graph Memory Application
```

---

Це дає нам можливість:

Наприклад, завтра:

```
DocHub

uses:

Graph Memory Core

+

Documentation Schema
```

і Core навіть не треба міняти.

## Principles

- Core schema-agnostic, schema engine validates structure
- Domain schemas are separate declarative definitions
- Core provides Entity Types, fields, Relations, Events, indexes
- Domain provides semantics for entities and relations
- Portability: swap domain schema without touching Core
- Extensibility: other domains reuse Core with own schema
- Schema evolution: Core supports versioned schema definitions

## Schema Concepts

### Entity Types
Generic definition of entity with name, fields, relations. Core validates structure without knowing domain meaning.

### Relations
Named connections between entities. Core stores and indexes relations.

### Events
Core tracks events for audit and change tracking.

### Validation
Schema engine validates structure against defined schema.

## Decision Status
Accepted
Date: 2026-08-20
Source: Split from ADR-012_Schema_Architecture_Decision.md — generic portion extracted
