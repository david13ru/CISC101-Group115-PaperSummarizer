<!-- Task 3 Update: Added explicit summary_level variable, conditional logic for "short" vs "detailed", and ensured detailed mode produces both a paragraph and a bullet list. -->

# Module 02 – Section Loop

## Purpose
Loop over each validated section and generate a section-level draft summary according to the requested detail level, without going beyond the evidence in the text.

---

## Required Variable

The section loop must respect the following control variable passed in from Module 01:

- `summary_level` — allowed values:
  - `"short"`
  - `"detailed"`

If `summary_level` is missing or invalid, default to `"short"`.

---

## Inputs Per Section

For each section in the normalized section list, the loop receives:

- `section_name`
- `section_text`
- `status_flags` (e.g., `missing`, `empty`, `too_short`)
- `summary_level`
- `evidence_mode` (expected to be `"strict"`)

---

## Skip & Warning Logic

Before drafting:

- **If `missing` or `empty`:**
  - Do **not** attempt a summary.
  - Output standardized warning:
    - `Section skipped: no usable text.`

- **If `too_short` (< 50 words):**
  - Attempt a summary, but append:
    - `Section short: summary may be incomplete.`

Warnings must be carried downstream for the Checks & Warnings output.

---

## Drafting Logic – Short Mode

If `summary_level == "short"`:

- **Form:**
  - Produce **1–2 sentences** total.
- **Focus:**
  - Capture the central purpose, claim, or result of the section.
- **Constraints:**
  - Use only information explicitly present in `section_text`.
  - Preserve important terminology and acronyms.

Example style (not literal text):

> "This section introduces the main objective of the study and outlines the high-level approach."

---

## Drafting Logic – Detailed Mode

If `summary_level == "detailed"`:

- **Output must include both:**
  1. **A single concise paragraph** (4–6 sentences)  
  2. **A bullet list** of **3–5 highlights**

- **Paragraph content:**
  - Summarize:
    - Objectives or questions
    - Methods or approach
    - Key signals or findings
    - Any explicit limitations mentioned in the section

- **Bullet list content:**
  - Each bullet must be directly supported by the text.
  - Focus on concrete details:
    - Specific methods
    - Datasets or settings
    - Reported results or effects
  - No invented numbers, methods, or context.

Structure example (not literal):

> Paragraph explaining the section in full sentences.  
>  
> - Bullet 1 – concrete detail from text  
> - Bullet 2 – concrete detail from text  
> - Bullet 3 – concrete detail from text  

---

## Evidence and Attribution

Regardless of `summary_level`:

- If `evidence_mode == "strict"`:
  - Every sentence in the summary and every bullet must be traceable to the section text.
  - Do not introduce background context, literature, or claims that are not clearly present.
- Ambiguous statements should be rephrased cautiously or explicitly flagged as uncertain if the source text is unclear.

---

## Outputs Per Section

For each section, the loop passes forward:

- The generated summary text
  - Short mode: 1–2 sentences
  - Detailed mode: paragraph + bullet list
- Any attached warning messages
- Extracted key terms / acronyms for the shared terminology ledger
