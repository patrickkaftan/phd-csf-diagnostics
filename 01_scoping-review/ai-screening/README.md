# AI-Assisted Screening

LLM prompt and methodology for AI-supported title/abstract screening (PRISMA-ScR Section 6.6).

## Approach

Parallel screening: human reviewer + Claude Opus 4.8 (temperature=0).  
Agreement analysis: sensitivity, specificity, Cohen's κ (human as reference standard).  
All divergences proceed to Phase 2 (full-text review).

## Disclosure

AI involvement disclosed in protocol header per PRISMA-ScR transparency requirements.  
References: Khraisha et al. (2024, *Res Synth Methods*); Ghossein et al. (2025, *JMIR Form Res*).

## Contents

- `screening_prompt.md` — prompt used for Include / Exclude / Uncertain classification with rationale
- `agreement_analysis.md` — Cohen's κ and sensitivity/specificity results (added post-screening)
