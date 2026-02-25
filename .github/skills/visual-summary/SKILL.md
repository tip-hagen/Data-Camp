---
name: visual-summary
description: Reads a transcript and/or exercise text and produces a markdown summary along with a simple visual aid (diagram or table) to accompany the notes.
---

# Visual Summary

This skill augments the **datacamp-summary** skill by adding lightweight visual representations - Mermaid diagrams or markdown tables - that make concepts more memorable. Always apply this skill **in combination** with datacamp-summary; do not use it standalone.

---

## Heading & Formatting Rules (CRITICAL)

Visual cells must follow the same bold-heading convention as the rest of the notebook. See the datacamp-summary skill for the full rule table. Summary:

- Use `**Visual Aid: {Descriptive Name}**` as the cell title - **not** `## Visual Aid`.
- Add one italicised caption sentence below the diagram explaining what it shows.

---

## One Diagram Per Cell (CRITICAL)

Placing multiple Mermaid blocks in a single cell causes them to **overlap and break rendering**. Every diagram or table must be in its **own separate notebook cell**.

| Rule | Correct | Wrong |
|---|---|---|
| Diagram isolation | One Mermaid block per cell | Two `mermaid` blocks in one cell |
| Cell title | `**Visual Aid: Name**` (bold) | `## Visual Aid` (heading) |
| Node labels | `["Multi word label"]` in quotes | `[Multi word]` unquoted |
| Newlines in labels | Use plain short text or separate nodes | `\n` inside a label string |
| Node text size | `classDef ... font-size:20px` | No classDef (renders too small) |

---

## Visual Cell Template

**For diagrams:**

```markdown
**Visual Aid: {Descriptive Name}**

*{One sentence explaining what the diagram shows.}*

```mermaid
graph LR;
    A(["Node Label"]) --> B(["Node Label"]);
    classDef styleA fill:#4285F4,stroke:#0F9D58,stroke-width:2px,font-size:20px;
    class A,B styleA;
```
```

**For tables:**

```markdown
**Visual Aid: {Descriptive Name}**

*{One sentence explaining what the table compares.}*

| Column 1 | Column 2 | Column 3 |
|---|---|---|
| value | value | value |
```

---

## Cell Placement

Visual cells are inserted **after Key Concepts and before the `---` separator**:

```
Cell 1  - Chapter Title
Cell 2  - Overview
Cell 3  - Key Concepts
Cell 4  - [Visual Aid: Diagram 1]   <- one cell per diagram
Cell 5  - [Visual Aid: Diagram 2]   <- one cell per diagram
Cell 6  - [Visual Aid: Table]       <- one cell per table
Cell 7  - ---  (separator)
Cell 8  - Exercise
```

---

## Mermaid Style Reference

Based on reference notebooks, apply `classDef` to every diagram for consistent node colours and readable font size. Always set `font-size:20px` in every `classDef`.

**Recommended fill colours:**

| Node type | Fill | Stroke |
|---|---|---|
| User / neutral | `#CCCCCC` | `#333` |
| Model / primary | `#4285F4` | `#0F9D58` |
| Tools / actions | `#DB4437` | `#F4B400` |
| External / data | `#A142F4` | `#333` |
| Orchestration | `#0F9D58` | `#333` |

---

## Fallback

If the content lacks clear relationships to diagram, use a **markdown table** instead. Never force a diagram onto flat comparison lists.

---

## Workflow

1. Read transcript and exercise files (delegated from datacamp-summary).
2. Identify components with relationships -> prefer **Mermaid diagram**.
3. Identify comparisons or criteria lists -> prefer **markdown table**.
4. Create one cell per visual, using the Visual Cell Template above.
5. Insert visual cells after Key Concepts, before the separator cell.

> **References:** See `.github/skills/visual-summary/references/` for completed example notebooks demonstrating correct diagram style and cell placement.
