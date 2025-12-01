<!-- Task 3 Update: Added explicit evidence_mode flag with strict evidence enforcement, plus standardized conditional warning messages for missing, empty, and short sections. -->

# Module 03 – Guardrails

## Purpose
Apply global safety checks to all section drafts so that:
- Every claim is supported by the original text.
- Standardized warning messages are attached when sections are missing, empty, or too short.
- Content is prepared for final rendering without hallucinations.

---

## Required Flag

This module assumes the following control flag is set by earlier modules:

- `evidence_mode` — allowed values:
  - `"strict"` (default and required for this project)

If a different value is provided, this module must reset it to `"strict"`.

---

## Strict Evidence Enforcement

If `evidence_mode == "strict"`:

1. **Sentence-level verification**
   - For each summary sentence and each bullet:
     - Check that the claim can be directly matched to phrases or facts in the corresponding `section_text`.
     - If it cannot be traced, **remove or rewrite** it to align exactly with available evidence.

2. **Terminology accuracy**
   - Ensure acronyms and key terms match the wording in the paper.
   - Do not substitute with new terminology that does not appear in the text.

3. **Numerical/data integrity**
   - Only keep numeric values, metrics, or statistical claims that are explicitly present.
   - Remove any inferred p-values, effect sizes, or “improvement” claims that are not clearly stated.

If a section becomes nearly empty after these checks, attach:

> `Insufficient information: claims limited; interpret with caution.`

---

## Warning Message Logic

Guardrails is responsible for attaching standardized warnings when certain conditions are met:

- **Missing or empty section:**
  - Attach:
    - `Section skipped: no usable text.`

- **Too short (< 50 words):**
  - Attach:
    - `Section short: summary may be incomplete.`

- **Insufficient evidence after filtering:**
  - Attach:
    - `Insufficient information: claims limited; interpret with caution.`

Multiple warnings can be combined if several conditions apply.

---

## Word-Limit Pre-check

Before passing drafts to Module 04:

- Identify any section drafts that currently exceed the **100–150 word** range for the final table.
- Mark these drafts with a flag such as `needs_trimming = true` so that Module 04 knows to shorten them while preserving:
  1. Objectives
  2. Methods
  3. Key findings
  4. Limitations

---

## Outputs

For each section, Guardrails outputs:

- A validated, evidence-compliant summary draft
- A list of all standardized warnings associated with the section
- Updated terminology and flags (including any `needs_trimming` markers)

These outputs are then used by Module 04 for final rendering.
