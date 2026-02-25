---
name: datacamp-summary
description: Reads a Datacamp transcript and exercise text files, then produces a notebook‑friendly markdown summary with an overview, key concepts, and exercise notes.
---

# Datacamp Summarizer

This skill helps the agent turn raw lesson materials (a `Transcript.txt` and an `Exercise.txt`) into a polished, markdown‑formatted summary suitable for inclusion in Jupyter notebooks. The summary is written as a neutral module overview rather than referencing a video or lecture.
**What the Skill Does**

- **Reads** the contents of a transcript and an exercise text file.
- **Synthesizes** the material into concise modules.
- **Outputs** a summary in markdown with example headings like `## Overview`, `## Key Concepts`, and `## Exercise Notes`.

**Inputs**

The agent can provide either:

1. **File paths** to `Transcript.txt` and `Exercise.txt`, or  
2. **Raw text content** from those files (e.g. inline copy/paste).

Both inputs are optional but at least one form of each file must be supplied.

**Output**

A single markdown string that:

- Is formatted with notebook‑friendly headings.
- Contains sections such as:

  ```markdown
  ## Overview
  ...brief conceptual introduction and examples...

  ## Key Concepts
  - concept one
  - concept two
  - …

  ## Exercise Notes
  …important hints or results from the exercise…
  ```

- Is concise (see tips below) and ready to drop into a `.ipynb` cell.

**When to Use This Skill**

Invoke this skill when the user wants an agent to:

- **Summarize a Datacamp lesson** for review, sharing, or study notes without mentioning the medium.
- **Transform transcripts/exercises** into readable documentation.
- **Prepare notebook content** as neutral module notes.

**Example Prompts**

- "Here are the transcript and exercise files. Can you create a module-style summary for a notebook?"
- "Read `Transcript.txt` and `Exercise.txt` and give me a markdown overview with key concepts."
- "Generate a concise conceptual summary of these texts for my notes."

**Sample Workflow**

1. **Read files**: load `Transcript.txt` and `Exercise.txt` (either from disk or from provided text).
2. **Identify key points** in the transcript: main topics, examples, definitions.
3. **Extract exercise insights**: what the task asked for, any notable output or errors.
4. **Compose markdown** sections:

   - `## Overview` – a paragraph or two capturing the main concept and examples.
   - `## Key Concepts` – bulleted list of the most important ideas.
   - `## Exercise Notes` – description of the exercise goal and any tips.

5. **Return** the assembled markdown string to the caller.

**Tips & Clarifications**

- **Length**: aim for brevity – a few sentences per section, and no more than 1–2 paragraphs in total.
- **Formatting**: use proper markdown headings and bullets; avoid raw code unless it’s part of an exercise note.
- **Manual Review**: summaries are generated automatically and may need tweaking; encourage the user to proofread.
- **Notebook‑friendly**: keep the output clean so users can paste it directly into a Jupyter cell without further editing.

> **Note:** This skill doesn’t execute code; it only interprets text files. If the transcript is very long, focus on high‑level themes rather than transcribing everything.