# Phase 1 Screening (Title/Abstract)

Tracking structure for Phase 1 title/abstract screening (PRISMA-ScR Section 6, protocol v2.1).
LLM prompt and methodology for AI-supported title/abstract screening (PRISMA-ScR Section 6.6).

Distinct from `data-charting/`: this stage records only eligibility decisions (I1-E7, Section 6.4) on a plausibility basis, not the content extraction variables (Section 7.2), which apply only to the final included corpus after full-text screening.

## AI-Assisted Approach

Parallel screening: human reviewer + Claude Opus 5.
Agreement analysis: sensitivity, specificity, Cohen's kappa (human as reference standard).
All divergences proceed to Phase 2 (full-text review).

## Disclosure

AI involvement disclosed in protocol header per PRISMA-ScR transparency requirements.
References: Khraisha et al. (2024, *Res Synth Methods*); Ghossein et al. (2025, *JMIR Form Res*).

## Contents

- `zotero_export_300.csv` — raw bibliographic export of the 300 deduplicated records (source: Zotero)
- `human_screening.xlsx` — Human screening file: bibliographic fields + `Human_Decision` / `Human_Rationale`. No AI columns.
- `ai_screening.xlsx` — AI screening file: bibliographic fields + `AI_Decision` / `AI_Rationale`. No human columns.
- `screening_prompt.md`: prompt used for Include / Exclude / Uncertain classification with rationale
- `agreement_analysis.md`: Cohen's kappa and sensitivity/specificity results (added post-screening)

## Why two separate files

Protocol Section 6.6: *"The AI screener operates independently of the human reviewer; its outputs are withheld from the human screener until Phase 1 is complete."* A shared file with both decision columns visible would break this independence assumption, which the agreement analysis (sensitivity, specificity, Cohen's kappa) in Section 6.6 relies on. Split as of 2026-08-05, before any screening decisions were recorded (both decision columns were still empty at time of split).
## Decision values

`Human_Decision` / `AI_Decision`: `Include`, `Exclude`, `Uncertain` (dropdown-validated in both files). Per protocol: uncertain → include; AI-flagged disagreements are carried forward to Phase 2 regardless of the human Phase 1 decision.
