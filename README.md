# CISC 101 — Paper Summarizer Final Project

This repository contains the completed final project for the CISC 101 Research Paper Summarizer system.  
The system was generated using a meta-prompt in Microsoft Copilot (Task 1), then revised and maintained in this GitHub repository (Task 2 & Task 3).

---

##  Repository Structure

| File / Folder | Description |
|--------------|-------------|
| `system_prompt.md` | Full system prompt generated from the meta-prompt |
| `/modules/` | Internal modular architecture used by the summarizer system |
| `01_intake_and_setup.md` | Input handling, section validation, flag initialization |
| `02_section_loop.md` | Loops through each section and drafts summaries based on detail level |
| `03_guardrails.md` | Strict evidence checks, warning enforcement, removal of unsupported content |
| `04_rendering_and_refinement.md` | Final formatted output assembly and word-limit enforcement |
| `05_citation_extractor.md` | Extracts only citations explicitly found in the text |
| `06_key_contributions_summarizer.md` | Identifies key contribution statements based on paper language |

---

## PS2 Specification Compliance

This project follows all required PS2 design principles, including:
- Structured inputs & outputs
- Strict hallucination prevention rules
- Word-limit enforcement
- Table-based section summaries
- Audience-specific summary generation
- Modular architecture inspired by Travel Planner

---

## Task 3 Updates

Modules 02 and 03 will be updated through a Pull Request with:
- Added `summary_level` conditional behavior (**short vs. detailed**)
- Added `evidence_mode = "strict"` logic and missing-section warnings

Screenshots of these changes will be included in the final submission document as required.

---

### Status

All repository components for Task 2 have been successfully created.  
Task 3 modifications will be completed via a branch + pull request workflow.

---

Thank you for reviewing this repository!
