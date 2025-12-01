# Module 03 – Guardrails

## Purpose
Verify all draft summaries remain fully evidence-bound and attach appropriate warnings.

---

## Required Variable
`evidence_mode = "strict"`

---

## Enforcement
- Check every claim against the provided text
- Remove unsupported or speculative content
- Preserve exact terms used in the paper

---

## Numerical & Data Checks
- No invented values or statistical claims
- No references unless present directly in text

---

## Standard Warnings
- “Section skipped: no usable text.”
- “Section short: summary may be incomplete.”
- “Insufficient information: claims limited; interpret with caution.”

---

## Pre-Render Word-Limit Guard
Flag any >150-word sections for trimming in Module 04.

---

## Output
- Cleaned validated drafts
- Updated warning list
- Updated glossary ledger
