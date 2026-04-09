# Page Templates

Use these templates when creating or substantially rewriting wiki pages.

## Concept Page

Path: `pages/concepts/*.md`

```markdown
# [Concept Name]

> Brief one-line definition

## Core Definition

[2-3 sentences defining the concept precisely]

## Key Properties

- Property 1: explanation
- Property 2: explanation

## In [Your Domain]

[How this concept manifests in your specific domain - implementation notes, examples]

## Related Concepts

- [[concept-related-1]] - relationship description
- [[concept-related-2]] - relationship description

## Sources

- [[source-spec-rest-api]] § section
- [[source-paper-consensus-raft]] § section
```

## Entity Page

Path: `pages/entities/*.md`

```markdown
# [Entity Name]

> One-line role description

## Purpose

[What this entity does in the system]

## Structure

[Fields, properties, data shape]

## Lifecycle

[How this entity is created, updated, destroyed]

## Related Entities

- [[entity-related-1]] - relationship
- [[entity-related-2]] - relationship
```

## Decision Page

Path: `pages/decisions/*.md`

```markdown
# Decision: [Short Title]

**Status**: Accepted | Proposed | Superseded
**Date**: YYYY-MM-DD
**Context**: [What triggered this decision]

## Decision

[The choice made]

## Rationale

[Why this choice - alternatives considered, trade-offs]

## Consequences

- Positive: ...
- Negative: ...
- Risks: ...

## Related

- [[decision-related-decision]] - related decision
- [[concept-related-concept]] - relevant concept
```

## Comparison Page

Path: `pages/comparisons/*.md`

```markdown
# [A] vs [B]

> Brief summary of the comparison

## Dimensions

| Dimension | [A] | [B] | Position |
|-----------|-----|-----|----------|
| X | ... | ... | ... |
| Y | ... | ... | ... |

## Analysis

[Synthesis of trade-offs, when each is appropriate]

## Sources

- [[source-spec-method-a]]
- [[source-spec-method-b]]
```

## Source Summary Page

Path: `pages/sources/*.md`

```markdown
# Source: [Title]

**Type**: spec | paper | article
**URL**: [original URL if web source]
**Date Added**: YYYY-MM-DD
**Key Sections**: §1, §2, §3

## Summary

[3-5 sentence summary of the source's main contribution]

## Key Extracts

> [Direct quotes or paraphrased key points]

## Related Concepts

- [[concept-related-1]] - how this source informs it
- [[concept-related-2]] - how this source informs it

## Impact

[How this source influenced understanding or decisions]
```

## Stub Page

Use when a concept needs a page but cannot yet be fully developed.

```markdown
# [Concept Name]

> [Brief definition from first mention]

## Status

Stub - needs expansion from sources: [[source-spec-auth-flow]], [[source-paper-consensus-raft]]

## Initial Notes

[Brief notes from current understanding]
```
