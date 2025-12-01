# Module 01 – Intake & Setup

## Purpose
Initialize controls, normalize section names, and detect missing or too-short sections. Guarantee that no external or hallucinated content is introduced.

---

## Inputs
- Section map `{section_name → section_text}`
- Audience level: “expert” or “general”
- Summary detail level: “short” or “detailed”

---

## Outputs
- Normalized section list
- Section status report
  - Missing
  - <50 words (“Section short: summary may be incomplete.”)
  - Empty (“Section skipped: no usable text.”)
- Control flags:
  - `summary_level`
  - `evidence_mode = "strict"`

---

## Normalization Rules
- Convert names to lowercase and trim whitespace
- Alias mapping common section names (e.g., Methods → Standard label)
- Allow custom section names when not recognized

---

## Status Detection
- Missing: Section name provided without text
- Too short: <50 words → warning flag added
- Empty: Text only whitespace → skip summary and warn

---

## Initialization
- Default summary level: “short” if unspecified
- Force strict evidence boundary
- Initialize terminology ledger for use across all modules

---

## Pass-down Contract
Provide normalized sections, flags, ledger, and control settings to Module 02.
