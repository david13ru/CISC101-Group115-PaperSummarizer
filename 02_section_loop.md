# Module 02 – Section Loop

## Purpose
Draft section summaries based on the requested detail level.

---

## Required Variable
`summary_level = "short"` or `"detailed"`

---

## Skip Logic
- Missing or empty → “Section skipped: no usable text.”
- Too-short <50 words → include summary but attach warning

---

## If `summary_level = "short"`
- 1–2 sentence compact summary
- Use only explicit info from text
- Preserve original terminology

---

## If `summary_level = "detailed"`
- One concise paragraph **plus** 3–5 bullet highlights
- Bullets must come directly from the section text
- No new information or inferred claims

---

## Evidence Enforcement
- Strict mode only: delete unsupported statements
- No invented citations, methods, or outcomes

---

## Output Per Section
- Draft summary form
- Warning text if applicable
- Candidate terms added to glossary ledger
