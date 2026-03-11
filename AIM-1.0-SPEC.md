Copyright 2026 Ludvig Alexander Munthe

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License in the LICENSE file distributed with this work.

Unless required by applicable law or agreed to in writing, this file
is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF
ANY KIND, either express or implied. See the License for the specific
language governing permissions and limitations under the License.

# AIM 1.0: AI Manual Format

AIM is a human-readable, AI-optimized structured text format for operational standards, control manuals, policy specs, and runtime guidance.

---

## 1. Purpose

AIM exists to make structured manuals easy for both:

- **AI systems** to parse, prioritize, and follow
- **Humans** to read, audit, and maintain

AIM is designed for documents that mix:

- stable metadata
- explicit section structure
- tagged semantic blocks
- procedural rules
- concise explanatory prose

AIM is not intended to replace JSON, YAML, Markdown, or code. It is intended for documents that need stronger semantic structure than plain text, while remaining more readable and flexible than rigid machine-only formats.

---

## 2. Design Goals

AIM should be:

- easy for AI systems to parse
- easy for humans to read
- stable under long-context use
- explicit about document structure
- compatible with plain text workflows
- tolerant of rich prose outside tagged blocks
- strict about canonical anchors

---

## 3. Canonical File Extension

The canonical file extension for AIM is:

```text
.aim
```

Examples:

```text
AEGIS-0.2.aim
RUNTIME-GUARDRAILS-1.0.aim
MEDICAL-STRICT-ADAPTER-0.4.aim
```

---

## 4. Encoding and Newline Rules

AIM files must follow these base formatting rules:

- encoding: **UTF-8**
- newline style: **LF**
- tab characters: **FORBIDDEN**
- trailing whitespace: **FORBIDDEN**
- blank lines: allowed for readability
- indentation: allowed for readability only, unless a higher-level spec defines semantic indentation

AIM is a **plain text first** format. It may be rendered in Markdown-aware environments, but its canonical structure does not depend on Markdown rendering.

---

## 5. Required Header

Every AIM file must begin with a header block.

Required header fields:

```text
FORMAT:
TOPIC:
GOAL:
TARGET:
MODE:
STATUS:
```

Canonical example:

```text
FORMAT: AIM 1.0
TOPIC: AEGIS: Spec-Grade AI Hallucination Prevention Standard V0.2
GOAL: Maintain AI precision by catching hallucinations immediately and debugging root causes
TARGET: AI chat models
MODE: Integrated single-file manual
STATUS: Spec-grade, taxonomy-driven, compressed, modular
```

### Header Rules

- Header fields must appear before all sections.
- Header keys must be uppercase.
- Header keys must end with `:`.
- Header values may contain spaces and punctuation.
- Unknown additional header keys are allowed, but required keys must appear exactly once.
- Required header keys should appear in the canonical order shown above.

---

## 6. Required Section Index

Each AIM file must declare its major sections near the top.

Canonical form:

```text
[INDEX:MANUAL:SECTIONS]
0 META
1 CORE_RULES
2 PILOT_COCKPIT_MODE
3 VOCABULARY
```

### Section Index Rules

- The section index must appear after the header.
- Section numbers must be ascending.
- Section names must be uppercase with underscores.
- Each numbered section in the index must correspond to a real section banner later in the file.
- No major section may appear in the file unless it appears in the section index.

---

## 7. Required Section Banner

Each major section must begin with a section banner.

Canonical form:

```text
================================================================
[SECTION 3: VOCABULARY]
Purpose:
- Define the core terms used throughout the standard.
- Establish stable canonical tokens for later sections.
================================================================
```

### Section Banner Rules

- Banner lines must use a strong visual delimiter.
- The section tag must follow this pattern:

```text
[SECTION N: SECTION_NAME]
```

- `N` must match the number declared in the section index.
- `SECTION_NAME` must match the section index entry exactly.
- A `Purpose:` field is REQUIRED.
- At least one purpose bullet is REQUIRED.

---

## 8. Optional Subsection Banner

Subsections are strongly recommended for long sections.

Canonical form:

```text
------------------------------------------------
[SUBSECTION:VOCABULARY:ACCURACY_TERMS]
Purpose:
- Define the core factual reliability terms.
------------------------------------------------
```

### Subsection Rules

- Subsection names should be uppercase with underscores.
- Subsections should remain inside their parent section.
- A `Purpose:` field is RECOMMENDED.
- Subsection banners do not appear in the top-level section index.

---

## 9. Tagged Semantic Blocks

AIM uses tagged semantic blocks to represent structured meaning.

Canonical examples:

```text
[TERM:ACCURACY:CLAIM]
Definition:
- Smallest factual unit that can be checked.
```

```text
[RULE:SYSTEM:INVARIANT_SUPPORT]
REQUIRED:
- No emitted factual claim may have verdict UNSUPPORTED.
```

```text
[WORKFLOW:DEBUG:HALLUCINATION_INCIDENT]
1. capture prompt, answer, sources, config
2. reproduce deterministically if possible
3. extract false or unsupported claims
```

### Common Canonical Tags

```text
[TERM:...]
[RULE:...]
[FUNC:...]
[COMPONENT:...]
[MECHANIC:...]
[STATE:...]
[WORKFLOW:...]
[REFERENCE:...]
[DECISION:...]
[CHECK:...]
[RECIPE:...]
[SUMMARY:...]
[EXAMPLE:...]
[BUG:...]
[NODE:...]
[ARCHETYPE:...]
[PREREQUISITE:...]
[RELATED:...]
[EXPANSION:...]
[DEPENDENCY:...]
[RELATION:...]
[INDEX:...]
[META:...]
```

---

## 10. Tag Grammar

Canonical AIM tag grammar:

```text
[TAG:FAMILY:NAME]
```

Extended forms are allowed:

```text
[TAG:FAMILY:SUBFAMILY:NAME]
[TAG:SCOPE:FAMILY:NAME]
```

### Tag Rules

- Tags must begin with `[` and end with `]`
- Tag segments are separated by `:`
- Tag segments must use uppercase letters, digits, or underscores
- spaces inside tag segments are **FORBIDDEN**
- hyphens inside tag segments are **FORBIDDEN**
- descriptive meaning belongs in the body, not the tag
- tag names should be stable once published

Valid examples:

```text
[TERM:ACCURACY:CLAIM]
[RULE:SYSTEM:FAIL_CLOSED_POLICY]
[WORKFLOW:DEBUG:HALLUCINATION_INCIDENT]
```

Invalid examples:

```text
[term:accuracy:claim]
[RULE:system:fail closed]
[WORKFLOW-DEBUG-HALLUCINATION_INCIDENT]
```

---

## 11. Field and Body Rules

Tagged blocks may contain:

- scalar fields
- bullet lists
- numbered sequences
- short paragraphs
- literal blocks

Canonical scalar fields:

```text
Definition:
Purpose:
Role:
Goal:
Rule:
Output:
Example:
```

### Field Rules

- field labels should end with `:`
- field labels should be capitalized consistently
- field labels may repeat within different block types
- field bodies may span multiple lines
- nested bullets are allowed
- numbered steps are allowed
- prose paragraphs are allowed after field labels

Canonical list style:

```text
- item one
- item two
- item three
```

Canonical numbered style:

```text
1. first
2. second
3. third
```

---

## 12. Literal Blocks

AIM may contain literal examples such as pseudocode, JSON, YAML, or sample text.

Literal blocks may be represented using fenced blocks in Markdown-aware environments:

```text
```json
{ "example": true }
```
```

Or by explicit field markers in plain-text-first contexts:

```text
JSON_SHAPE:
{
  "example": true
}
```

### Literal Block Rules

- Literal blocks must remain clearly visually separated from surrounding fields
- Literal content is not parsed as AIM tags unless explicitly stated
- A tag-looking string inside a literal block is treated as literal content

---

## 13. Comments and Annotations

AIM 1.0 does **not** define a formal comment syntax.

Reason:
- comment styles vary across editors and downstream parsers
- comment semantics can create ambiguity in AI-facing documents

Recommendation:
- use explicit annotation blocks instead of comments

Examples:

```text
[NOTE:FORMAT:RATIONALE]
[BUG:SYSTEM:KNOWN_LIMITATION]
[SUMMARY:SECTION:KEY_IDEAS]
```

If a downstream toolchain wants comments, it must define them as an extension profile, not as base AIM 1.0 behavior.

---

## 14. Ordering Rules

Canonical order for an AIM file:

1. required header
2. top-level section index
3. section banners in ascending order
4. subsection banners and tagged blocks within each section
5. summaries or end matter if needed

### Ordering Constraints

- no section may appear before the section index
- no tagged block may appear before a major section, except the header and section index
- section order must match the section index order
- subsection order is flexible within a section unless constrained by a higher-level spec
- repeated core rules must preserve canonical wording

---

## 15. Repetition Rule

Core invariants may repeat across an AIM document.

However:

- repeated wording for the same hard rule should remain **canonical**
- paraphrased restatements of the same invariant should be avoided in AI-facing sections
- human-facing summaries may restate ideas more freely if clearly separated from the canonical manual

Good repetition:

```text
No emitted factual claim may have verdict UNSUPPORTED.
```

Bad repetition:

```text
Unsupported facts should probably not be emitted.
```

---

## 16. Validation Rules

An AIM 1.0 file is **valid** if it satisfies all REQUIRED conditions:

### REQUIRED

- valid UTF-8 plain text
- required header keys present exactly once
- section index present
- at least one section banner present
- section banners match the section index
- tags follow valid AIM tag grammar
- no tabs
- no trailing whitespace

### INVALID if any of the following occur

- missing `FORMAT:` header
- missing section index
- duplicate required header key
- section index and actual section numbers disagree
- malformed tag syntax
- section banners out of order
- tab characters present

### Unknown Tags

Unknown tags are allowed if they follow valid tag grammar.

This supports extensibility.

However:
- systems that rely on specific tags may ignore unknown tags
- conformance to a higher-level manual may restrict unknown tags

---

## 17. Conformance Levels

AIM defines three format conformance levels.

### AIM-Minimal

Required:
- header
- section index
- valid section banners
- valid tags
- plain text compliance

### AIM-Standard

Required:
- all AIM-Minimal requirements
- subsection banners for long sections
- stable field labels
- canonical ordering
- no malformed literal blocks

### AIM-Strict

Required:
- all AIM-Standard requirements
- canonical repeated wording for invariants
- no unknown tags unless declared
- stable tag registry for the document
- fully consistent section naming and field casing

---

## 18. Extensibility

AIM is intentionally extensible.

Allowed extension mechanisms:

- additional header keys
- additional tag families
- stricter project-level ordering rules
- stricter field-label vocabularies
- comment syntax defined by extension profile
- parser-specific validation profiles

Recommended extension declaration:

```text
FORMAT: AIM 1.0
PROFILE: PROJECT_NAME STRICT
```

---

## 19. Relationship to Markdown

AIM is not a Markdown dialect.

AIM may be stored inside Markdown files or rendered in Markdown-aware tools, but its canonical structure is:

- plain text
- section banners
- bracketed semantic tags
- structured fields and lists

Markdown is a display convenience. AIM is the document logic.

---

## 20. Relationship to Human-Facing Documents

AIM is intended primarily for AI-facing operational manuals, but it should remain human-readable.

Recommended repository split:

- `README.md` for the human-facing introduction
- `.aim` files for canonical AI-facing manuals
- supporting `.md`, `.json`, `.yaml`, or code files as needed

---

## 21. Minimal Valid AIM Example

```text
FORMAT: AIM 1.0
TOPIC: Example Manual
GOAL: Demonstrate the smallest valid AIM file
TARGET: AI systems
MODE: Single-file manual
STATUS: Draft

[INDEX:MANUAL:SECTIONS]
0 META
1 CORE_RULES

================================================================
[SECTION 0: META]
Purpose:
- Define document usage.
================================================================

[META:USAGE:BASIC]
Use:
- Read as an operating spec.

================================================================
[SECTION 1: CORE_RULES]
Purpose:
- Define one hard rule.
================================================================

[RULE:SYSTEM:INVARIANT_SUPPORT]
REQUIRED:
- No emitted factual claim may have verdict UNSUPPORTED.
```

---

## 22. Recommended Best Practices

- keep section names stable
- keep tags canonical
- repeat hard rules exactly
- use subsection banners for long sections
- separate human explanation from AI control logic when possible
- avoid decorative variation in AI-facing blocks
- treat AIM files as canonical operating artifacts, not casual notes

---

## 23. Non-Goals

AIM 1.0 does not attempt to provide:

- full machine validation semantics for every possible domain
- a replacement for JSON or YAML data exchange
- a formal programming language
- a universal documentation standard
- automatic syntax highlighting support across editors

---

## 24. Versioning

AIM format versions should use semantic-style major/minor notation.

Examples:

```text
AIM 1.0
AIM 1.1
AIM 2.0
```

Guidance:

- patch-level corrections may be handled informally in supporting docs
- minor version changes should preserve broad backward readability
- major version changes may alter structure or validation expectations

---

## 25. Summary

AIM 1.0 is a plain-text, AI-optimized manual format for structured operational documents.

Its core ideas are:

- explicit metadata
- explicit section boundaries
- tagged semantic blocks
- stable canonical wording
- human readability
- AI-friendly structure

In short:

> AIM is a format for manuals that both humans and AI systems can follow, but that gives AI systems stronger rails than plain prose alone.