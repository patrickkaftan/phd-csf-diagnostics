# Knowledge-Based Decision Support in CSF Diagnostics – Design Principles for an Integrated System Architecture Based on Clinical Guidelines and Routine Data

**Patrick Kaftan** | Doctoral Research (Dr. rer. nat.)  
Bielefeld University, Medical School OWL
Doctoral period: 01 August 2026 – 31 July 2029

---

## Overview

This repository contains the research documentation for a doctoral project developing an AI-based framework for cerebrospinal fluid (CSF) diagnostics. The framework integrates evidence-based medical knowledge from clinical practice guidelines with real-world decision logic from clinical routine data, operationalised at the point of care.

The system architecture follows three layers:

```
Knowledge Structuring (MKG) → Causal Inference (CPS) → Clinical Operationalisation (CDSS)
```

The research follows the **Design Science Research** paradigm (Hevner et al., 2004; Peffers et al., 2007) and produces prescriptive design knowledge (λ-knowledge) through iterative artefact design, demonstration, and evaluation.

**Clinical focus:** CSF diagnostics (OPS 1-204) for differential diagnosis across the neurological disease spectrum.  
**Clinical guideline:** AWMF 030/141 – Lumbar Puncture and CSF Diagnostics (v2, 2026).  
**Dissertation format:** Cumulative dissertation, minimum 3 first-author publications in English.

---

## Repository Structure

```
phd-csf-diagnostics/
├── 01_scoping-review/      # Publication 1 – Scoping Review (Eval Cycle 1, 2026)
│   ├── protocol/           # SLR protocol (PRISMA-ScR), registered before first search
│   └── search-strings/     # Database-specific search strings + hit counts
|   └── ai-screening/       # LLM prompt used for ai-supported screening
|   └── data-charting/      # Charting Table
|   └── references/         # List of references
│
├── 02_mkg/                 # Medical Knowledge Graph
│   ├── annotation-prompt/  # LLM prompts used for semantic code annotation
│
└── 03_cdss/                # CDSS / Dashboard
    └── requirements/       # Requirements specification

```

**Related repository:** [LiquorDiagnosticsDashboard](https://github.com/patrickkaftan/LiquorDiagnosticsDashboard) — CDSS dashboard implementation (Python, Dash/Plotly)

---

## Infrastructure

- **Data source:** [Data integration centres | Medical Informatics Initiative](https://www.medizininformatik-initiative.de/en/consortia/data-integration-centres)
- **Standards:** [Central terminology server | BfArM](https://terminologien.bfarm.de/index.html): ICD-10-GM, LOINC - Linguistic Variant, OPS
- **Data model:** [Core data set | Medical Informatics Initiative](https://www.medizininformatik-initiative.de/en/medical-informatics-initiatives-core-data-set)

---

## License

Documentation, methodology files, and prompts in this repository are licensed under  
**Creative Commons Attribution 4.0 International (CC BY 4.0)**.  
See [LICENSE](LICENSE) for details.

---

## Citation

If you use materials from this repository, please cite using the metadata in [CITATION.cff](CITATION.cff).  
GitHub renders this automatically as a **"Cite this repository"** button.
