---
name: datacamp-summary
description: Reads a Datacamp transcript and exercise text files, then produces a notebook-friendly markdown summary with an overview, key concepts, and exercise notes.
---

# Datacamp Summarizer

This skill turns raw lesson materials (`Transcript.txt` and `Exercise.txt`) into a polished, multi-cell Jupyter notebook summary. Summaries are written as neutral module notes - never referencing a video or lecture.

---

## Heading & Formatting Rules (CRITICAL)

All reference notebooks use **bold text** for every title and section header. Markdown heading syntax (`#`, `##`, `###`) is **never used**. Any agent producing `#`-style headings will create output that is visually inconsistent with the course style.

| Element | Correct | Wrong |
|---|---|---|
| Chapter / section title | `**Bold Title**` | `# Title` or `## Title` |
| Sub-section label | `**Bold Sub-section**` | `### Sub-section` |
| Divider between major sections | `---` in its own cell | blank lines only |
| Bullet term + definition | `- **Term**: description` | `- term: description` |

> **Reference:** Open any notebook in `.github/skills/datacamp-summary/references/` to see this style in action.

---

## Notebook Cell Structure (Template)

Each summary must be spread across **separate cells** in this exact order:

### Cell 1 - Chapter Title
```markdown
**{Course Chapter Title}**

{One-line description of the chapter topic. Include instructor name if relevant.}
```

### Cell 2 - Overview
```markdown
**Overview**

{2-4 sentences summarising the main concept, key example used, and what the learner gains. No bullet points - prose only.}
```

### Cell 3 - Key Concepts
```markdown
**Key Concepts**

- **{Term}**: {one-line definition or explanation}
- **{Term}**: {one-line definition}
- ...
```

> If the **visual-summary** skill is also active, visual cells are inserted **after Cell 3 and before Cell 4**.

### Cell 4 - Separator
```markdown
---
```

### Cell 5 - Exercise
```markdown
**Exercise: {Exercise Title}**

{Brief scenario description - 2-3 sentences.}

**Question:** {Question text}

- (1) {Option}
- (2) {Option}
- (3) **{Correct option - wrapped in bold}**
- (4) {Option}

*Answer: ({number})*
```

---

## Inputs

1. **File paths** to `Transcript.txt` and `Exercise.txt`, or
2. **Raw text content** from those files.

Both are optional but at least one form of each must be supplied.

---

## Sample Workflow

1. **Read** `Transcript.txt` and `Exercise.txt`.
2. **Identify**: chapter title, main concept, key example, terms, and definitions.
3. **Compose** cells following the Cell Structure template above - bold headings only, no `#` syntax.
4. **Extract** exercise: scenario, answer options, and correct answer from `Exercise.txt`.
5. **Insert** each section as a separate notebook cell.

---

## Tips & Clarifications

- **Bold, not headings**: `**Title**` is the intentional style of the course reference notebooks.
- **One concept per cell**: keep each cell focused; visual aids always get their own cells.
- **Brevity**: a few sentences per section; do not transcribe the full lesson.
- **Manual Review**: generated content may need tweaking - prompt the user to proofread.

> **References:** See `.github/skills/datacamp-summary/references/` for completed example notebooks demonstrating correct style.
