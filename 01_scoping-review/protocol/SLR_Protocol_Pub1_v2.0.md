# SLR Protocol — Pub. 1 (v2.0)
## Integrating Clinical Practice Guidelines and Electronic Health Records for Structured Clinical Inference: A Scoping Review

**Version:** 2.0  
**Date:** 2026-06-29  
**Author:** Patrick Kaftan  
**Institution:** Universität Bielefeld, Medizinische Fakultät OWL / Universitätsklinikum OWL / Klinikum Lippe  
**Project:** Dissertation  
**Target Journal:** Journal of Biomedical Informatics  
**PRISMA Standard:** PRISMA-ScR (Tricco et al., 2018, *Ann Intern Med*)  
**Predecessor:** SLR_Protocol_Pub1_v1.11.md  
**AI Assistance (Protocol Development):** Claude Sonnet 4.6 (claude-sonnet-4-6; Anthropic, accessed 2026-06-29)  
**AI Screening (Phase 1):** Claude Opus 4.8 (claude-opus-4-8; Anthropic; access date to be documented at time of search)  

> This protocol is timestamped and committed to Git prior to the commencement of database searching.  
> Deviations from the protocol will be transparently declared in the final manuscript.

---

## 1. Background and Rationale

Existing clinical decision support systems (CDSS) evaluate findings in a threshold-based and reactive manner, without modelling the complex decision logic that underlies a complete diagnostic process. Clinical decisions are substantially dependent on the variable context of individual patients — on the constellation of their findings, the dynamics of temporal progression, and the overall clinical presentation. This variability can be captured neither by universal rules alone nor by purely statistical associations.

Clinical guidelines encode this decision logic explicitly as normative rule structures; clinical routine data (EHR) represent the individual, time-varying patient context. Both knowledge sources are of central importance for clinical decision support because they form the basis on which diagnoses are made, prognoses derived, and treatment recommendations formulated. Which computational inference methods are capable of deriving such conclusions in a structured manner from the variable patient context has not yet been systematically investigated.

This scoping review maps — without technological presupposition — which methods are capable of deriving medical conclusions and predictions from variable clinical data, drawing on clinical guidelines, electronic health records, or both. A scoping review is the appropriate design because the objective is to chart the breadth of available inference mechanisms rather than to assess their comparative effectiveness — the defining application of scoping methodology as described by Arksey & O'Malley (2005) and operationalised in PRISMA-ScR (Tricco et al., 2018).

---

## 2. Research Question

**Primary Research Question:**

> *Which explicit, structured inference mechanisms have been proposed to derive medical predictions and conclusions from the complex, multi-parametric clinical context of individual patients, using clinical practice guidelines, electronic health records, or both?*

**Sub-questions:**

> *TF1 — How are these mechanisms evaluated — what clinical tasks, datasets, and performance metrics are used?*

> *TF2 — Through which specific approaches do these mechanisms produce interpretable outputs?*

> *TF3 — What are the research gaps, particularly in mechanisms that integrate both knowledge sources?*

---

## 3. PCC Framework

| Element         | Description                                                                                                                                                                                           |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **P** — Process | Clinical settings and healthcare contexts in which diagnostic or clinical decision-making requires inference over multi-parametric patient data                                                       |
| **C** — Concept | Explicit, structured computational inference mechanisms that derive medical predictions, diagnoses, or clinical recommendations from clinical practice guidelines, electronic health records, or both |
| **C** — Context | Any medical domain and clinical setting; no geographic or specialty restriction                                                                                                                       |

---

## 4. Eligibility Criteria

Inclusion and exclusion criteria are structured as mirror pairs (I*n* ↔ E*n*) and derived directly from the research question and the PCC framework.

| ID | Inclusion Criterion | ID | Exclusion Criterion |
|---|---|---|---|
| I1 | Peer-reviewed primary research proposing, implementing, or evaluating a computational inference mechanism | E1 | Secondary literature (reviews, meta-analyses, editorials, opinion papers) or non-peer-reviewed publications (abstracts, preprints) |
| I2 | Explicit, structured inference mechanism with inspectable reasoning process | E2 | Purely correlative ML model without symbolic or structured reasoning component |
| I3 | Utilizes clinical practice guidelines, EHR data, or both as knowledge source | E3 | Exclusively non-clinical data (e.g., imaging or genomics without clinical context) |
| I4 | Processes multiple clinical variables simultaneously (multi-parametric input) | E4 | Single-parameter threshold evaluation only |
| I5 | Produces medical predictions, diagnoses, prognoses, or treatment recommendations | E5 | No clinical decision or recommendation as output |
| I6 | Full text available in English or German | E6 | Full text not available in English or German |
| I7 | Published 2016–2026 | E7 | Published before 2016 |

---

## 5. Information Sources and Search Strategy

### 5.1 Databases

| Database                       | Field Syntax            | Rationale                                                                     |
| ------------------------------ | ----------------------- | ----------------------------------------------------------------------------- |
| Web of Science Core Collection | TS=                     | Broad interdisciplinary coverage; empirically tested in v1.x                  |
| PubMed (MEDLINE)               | [Title/Abstract]        | Medical informatics core literature                                           |
| Embase                         | :ti,ab                  | Stronger coverage of European and clinical-informatics literature than PubMed |

> **IEEE Xplore and ACM Digital Library were excluded from the search strategy following pilot searches.** Relevant conference papers from medical informatics venues (AMIA Annual Symposium, IEEE CBMS, MedInfo) are indexed in PubMed/MEDLINE and Web of Science. Pilot searches demonstrated that the unique contribution of both databases is minimal given their overlap with PubMed and WoS. Remaining gaps are addressed through citation tracing (Section 6.5).

### 5.2 Search Strategy

The search string was structured as a three-block Boolean query (Block A AND Block B AND Block C), with each block operationalizing a distinct conceptual dimension of the research question. A free-text strategy without controlled vocabulary (MeSH/EMTREE) was applied uniformly across all three databases to ensure methodological comparability.

Block C operationalizes the knowledge source criterion established in the research question. The terms "guideline*", "electronic health record*", "electronic medical record*", "EHR", and "clinical data" were retained on the basis of empirical pilot searches. Candidate terms including "routine data", "medical data", "health data", and "clinical record*" were tested and yielded either zero incremental hits or results whose relevance could not be confirmed. "Guideline*" was adopted as an umbrella term, fully subsuming more specific variants ("clinical guideline*", "practice guideline*") that produced no unique results.

Block B operationalizes the clinical decision support context. The terms "decision support", "CDSS", and "clinical pathway*" were retained. "Decision support" subsumes compound variants ("clinical decision support", "diagnostic decision support"), which proved redundant. The term "diagnosis" was empirically tested and not adopted: it produced an estimated false positive rate of 65–70%, predominantly comprising Bayesian network meta-analyses, imaging studies, and research studies without an explicit decision support frame. Studies addressing diagnostic reasoning without CDSS terminology are instead captured through structured citation tracing applied to all included studies, which constitutes the methodologically preferable alternative to search string expansion under high noise conditions.

The most consequential design decision concerned Block A, which operationalizes the computational method dimension. Four conceptually distinct approaches were systematically considered before a final design was adopted.

| Approach | Block A Terms | Core Problem |
|---|---|---|
| a) Representation Architecture | knowledge graph*, computer-interpretable guideline* | Does not distinguish construction vs. inference; not technology-agnostic |
| b) Inferential Function | reasoning, inference, prediction | Excludes papers that describe inference architecturally |
| c) Method Taxonomy | Bayesian network*, GNN, HMM, Markov logic... | Circular: presupposes what the review is intended to discover |
| d) Reasoning Paradigm | probabilistic, rule-based, causal, embedding* | Excludes papers that describe paradigms architecturally |

A combination of Approaches A and B — Representation Architecture and Inferential Function — would yield the most targeted retrieval for the specific system architecture under investigation in this dissertation. By jointly requiring both a structural representation term and an explicit inference qualifier, this combination reliably distinguishes papers proposing MKG- and CIG-based clinical inference from those in which knowledge graph construction is the primary contribution rather than graph-based reasoning. For a review scoped to these architectural families, the A+B combination would produce a corpus of high immediate relevance with comparatively low noise. However, this specificity is methodologically incompatible with the foundational commitment of the present review to technology-agnosticism.

### 5.3 Concept Blocks

**Block A — Inference Mechanism** *(Approach C: taxonomy-level terms, paradigm-representative selection):*

```
"knowledge graph*" OR "computer-interpretable guideline*"
OR "bayesian network*" OR "random field*" OR "markov model*"
OR "causal model*" OR "directed acyclic graph*"
OR "graph neural network*" OR "graph embedding*"
OR "neuro-symbolic" OR "probabilistic graphical model*"
```

> Terms were selected to represent each inference paradigm identified in the taxonomy (Section 5.2): *probabilistic* (bayesian network\*, random field\*, markov model\*, probabilistic graphical model\*); *rule-based* (computer-interpretable guideline\*); *causal* (causal model\*, directed acyclic graph\*); *embedding/connectionist* (graph neural network\*, graph embedding\*); *hybrid* (neuro-symbolic). Selection is restricted to paradigm-representative terms to mitigate the circularity risk of Approach C (Section 5.2). **Confirmed WoS hit count (2026-06-29): n=196.**

**Block B — Clinical Context:**

```
"decision support" OR "CDSS" OR "clinical pathway*" OR "diagnostic reasoning"
```

> "Decision support" subsumes compound variants ("clinical decision support", "diagnostic decision support"), empirically confirmed redundant in pilot searches. "Diagnostic reasoning" captures papers framing the task in cognitive rather than system terms.

**Block C — Knowledge Source:**

```
"guideline*" OR "electronic health record*" OR "electronic medical record*" OR "EHR" OR "clinical data"
```

> "Guideline\*" adopted as umbrella term, subsuming "clinical guideline\*" and "practice guideline\*" (no unique results in pilot searches). "Routine data", "medical data", "health data", and "clinical record\*" yielded zero incremental hits or results of unconfirmable relevance and were excluded.

### 5.4 Database-Specific Search Strings

#### Web of Science Core Collection

```
TS=("knowledge graph*" OR "computer-interpretable guideline*"
    OR "bayesian network*" OR "random field*" OR "markov model*"
    OR "causal model*" OR "directed acyclic graph*"
    OR "graph neural network*" OR "graph embedding*"
    OR "neuro-symbolic" OR "probabilistic graphical model*")
AND
TS=("decision support" OR "CDSS" OR "clinical pathway*" OR "diagnostic reasoning")
AND
TS=("guideline*" OR "electronic health record*" OR "electronic medical record*"
    OR "EHR" OR "clinical data")
AND PY=(2016-2026)
```

#### PubMed (MEDLINE)

```
(
  "knowledge graph*"[Title/Abstract] OR "computer-interpretable guideline*"[Title/Abstract]
  OR "bayesian network*"[Title/Abstract] OR "random field*"[Title/Abstract]
  OR "markov model*"[Title/Abstract] OR "causal model*"[Title/Abstract]
  OR "directed acyclic graph*"[Title/Abstract] OR "graph neural network*"[Title/Abstract]
  OR "graph embedding*"[Title/Abstract] OR "neuro-symbolic"[Title/Abstract]
  OR "probabilistic graphical model*"[Title/Abstract]
)
AND
(
  "decision support"[Title/Abstract] OR "CDSS"[Title/Abstract]
  OR "clinical pathway*"[Title/Abstract] OR "diagnostic reasoning"[Title/Abstract]
)
AND
(
  "guideline*"[Title/Abstract] OR "electronic health record*"[Title/Abstract]
  OR "electronic medical record*"[Title/Abstract] OR "EHR"[Title/Abstract]
  OR "clinical data"[Title/Abstract]
)
AND ("2016/01/01"[Date - Publication] : "2026/12/31"[Date - Publication])
```

#### Embase

```
(
  'knowledge graph*':ti,ab OR 'computer-interpretable guideline*':ti,ab
  OR 'bayesian network*':ti,ab OR 'random field*':ti,ab OR 'markov model*':ti,ab
  OR 'causal model*':ti,ab OR 'directed acyclic graph*':ti,ab
  OR 'graph neural network*':ti,ab OR 'graph embedding*':ti,ab
  OR 'neuro-symbolic':ti,ab OR 'probabilistic graphical model*':ti,ab
)
AND
(
  'decision support':ti,ab OR 'CDSS':ti,ab
  OR 'clinical pathway*':ti,ab OR 'diagnostic reasoning':ti,ab
)
AND
(
  'guideline*':ti,ab OR 'electronic health record*':ti,ab
  OR 'electronic medical record*':ti,ab OR 'EHR':ti,ab OR 'clinical data':ti,ab
)
AND [2016-2026]/py
```

> IEEE Xplore and ACM Digital Library: excluded per Section 5.1.

---

## 6. Screening Procedure

### 6.1 Phase Structure

```
Database search (WoS, PubMed, Embase)
        │
        ▼
Deduplication
        │
        ▼
Phase 1 — Title/Abstract Screening
  Human screener + AI screener (parallel, independent; Section 6.6)
  Criteria: I1–I7 / E1–E7 (plausibility-based)
  Uncertainty rule: include if uncertain
        │
        ▼
Phase 2 — Full-Text Screening
  Criteria: full operationalisation of all eligibility criteria
  Exclusion reason documented per paper
        │
        ▼
Final Inclusion List
        │
        ▼
Citation Tracing (Section 6.5)
```

### 6.2 Screeners

- **Primary screening:** Patrick Kaftan
- **AI-assisted parallel screening:** Claude Opus 4.8 (claude-opus-4-8; Anthropic) — Phase 1 title/abstract screening only; no decision authority (Section 6.6)
- **Second reviewer:** [TBD] — consensus process and 20% independent validation charting (Section 7.1)

### 6.3 Deduplication

- Tool: Zotero (automatic duplicate detection + manual verification)
- Export format: RIS from all three databases, imported into Zotero
- Deduplication prior to Phase 1 screening

### 6.4 Screening Rules

**Phase 1 (Title/Abstract)**
- Eligibility criteria I1–I7 / E1–E7 applied on a plausibility basis
- Uncertainty rule: *include if uncertain* — exclusion deferred to full-text screening
- No abstract available → flag for Phase 2

**Phase 2 (Full Text)**
- Full operationalisation of all eligibility criteria
- Exclusion reason documented per paper (PRISMA-ScR)
- Borderline cases I2 vs. E2: decision justified in screening log

Screening decisions are made by consensus between both reviewers. Disagreements are resolved through discussion with reference to the eligibility criteria (Section 4). All decisions are documented in the screening log.

### 6.5 Citation Tracing

Following completion of Phase 2:
- **Backward search:** reference lists of all included papers
- **Forward search:** papers citing included papers (via WoS / Google Scholar)
- Same eligibility criteria apply; results reported as "additional records" in the PRISMA flow diagram

### 6.6 AI-Assisted Parallel Screening

An LLM-based screener is applied in parallel to Phase 1 (title/abstract screening) to provide an independent validation signal and reduce the single-reviewer recall risk documented in Section 10. The AI screener operates independently of the human reviewer; its outputs are withheld from the human screener until Phase 1 is complete.

**Model and reproducibility:** The model used is Claude Opus 4.8 (model string: claude-opus-4-8; Anthropic). The access date is documented at the time of execution and reported in the manuscript. The complete prompt is provided as supplementary material to the manuscript.

**Prompt design:** The prompt operationalises the eligibility criteria (Section 4) as structured decision rules. For each title/abstract, the model outputs *Include* / *Exclude* / *Uncertain* with a mandatory one-sentence rationale. *Uncertain* classifications are treated as *Include*, consistent with the human uncertainty rule (Section 6.4).

**Agreement analysis:** Following completion of Phase 1, AI and human decisions are compared. Sensitivity (recall of included records), specificity, and Cohen's κ are calculated with the human decision as the reference standard. Results are reported in the manuscript and serve as a quantitative reliability indicator for the screening process.

**Disagreement resolution:** All records where AI and human decisions diverge are carried forward to Phase 2 for full-text review. The human reviewer retains final decision authority in all cases. The AI screener has no autonomous exclusion authority.

**Rationale and precedent:** LLM-assisted title/abstract screening has demonstrated feasibility across multiple review types. Khraisha et al. (2024) showed GPT-4 achieves human-comparable performance in screening tasks across peer-reviewed and grey literature in multiple languages (*Res Synth Methods*, doi:10.1002/jrsm.1715). Ghossein et al. (2025) evaluated multiple LLMs — including Claude — for citation screening against predefined eligibility criteria, reporting variable but promising agreement levels (*JMIR Form Res*, PMC11970706). Its application here serves two functions: (1) reducing recall loss inherent in single-primary-screener designs, and (2) generating quantitative agreement metrics that strengthen methodological transparency. This approach follows the principle of AI assistance rather than AI replacement as recommended in emerging guidelines for AI use in evidence synthesis.


---

## 7. Data Charting

### 7.1 Process

- Charting by Patrick Kaftan; second reviewer ([TBD]) charts 20% of papers independently for validation
- Tool: structured charting form (Excel)
- Piloted on 5 included papers prior to full charting; charting form revised as needed

### 7.2 Charting Fields

| Field                                | Description                             | Format / Options                                               |
| ------------------------------------ | --------------------------------------- | -------------------------------------------------------------- |
| Paper ID                             | Internal reference                      | P001, P002, …                                                  |
| Authors, Year                        |                                         |                                                                |
| Journal / Conference                 |                                         |                                                                |
| Study Type                           |                                         | System Design / PoC / Evaluation                               |
| Inference Paradigm                   | Assignment to taxonomy (Section 5.2)    | Rule-based / Probabilistic / Causal / Embedding / Hybrid       |
| Specific Mechanism                   | Concrete method or architecture         | Free text                                                      |
| Knowledge Source — Guidelines        | Guidelines used as input                | Yes / No / Unclear                                             |
| Knowledge Source — EHR               | EHR / routine data used as input        | Yes / No / Unclear                                             |
| Clinical Domain                      | Medical specialty / condition           | Free text                                                      |
| Clinical Task                        | Nature of clinical output               | Diagnosis / Prognosis / Treatment Recommendation / Other       |
| Evaluation — Task Type (TF1)         | How the mechanism was evaluated         | Clinical Validation / Expert Assessment / Simulation / None    |
| Evaluation — Dataset (TF1)           | Data used                               | Real / Synthetic / Not Specified                               |
| Evaluation — Metrics (TF1)           | Reported performance measures           | Free text                                                      |
| Interpretability — Approach (TF2)    | Interpretable output addressed          | Explicit / Implicit / Not addressed                            |
| Interpretability — Method (TF2)      | Concrete implementation                 | Free text                                                      |
| Integration of Both Sources (TF3)    | Guidelines + EHR combined               | Yes / Partial / No                                             |
| TRL                                  | Technology Readiness Level              | 1–9                                                            |
| Limitations (as reported by authors) |                                         | Free text                                                      |

---

## 8. Quality Assessment

Quality appraisal is not conducted in this scoping review. PRISMA-ScR (Item 18) explicitly exempts scoping reviews from quality assessment, consistent with the objective of mapping the breadth of available evidence rather than evaluating comparative effectiveness. Study type and Technology Readiness Level (TRL) are captured as data fields in the charting form (Section 7.2) to contextualise synthesis interpretations.

---

## 9. Synthesis Method

Meta-analysis is not applicable given the methodological and clinical heterogeneity of the corpus. The synthesis combines two complementary approaches:

**1. Taxonomic Classification Matrix**
All included papers are systematically classified according to the charting fields (Section 7.2): inference paradigm, knowledge sources, evaluation approach, interpretability approach, integration of both sources, TRL. The matrix constitutes the primary results table and enables direct comparison across the entire corpus.

**2. Narrative Synthesis**
Building on the classification matrix, the narrative synthesis addresses the three sub-questions:
- TF1: Under what conditions and with what metrics are the mechanisms evaluated?
- TF2: Through which specific approaches do these mechanisms produce interpretable outputs?
- TF3: What research gaps exist, particularly regarding the integration of both knowledge sources?

The synthesis follows the principle of descriptive completeness before evaluative judgement: systematic characterisation of the corpus precedes the derivation of patterns and gaps.

---

## 10. Limitations

**Language bias:** Inclusion is restricted to publications in English or German (I6/E6). Relevant work in other languages is not represented.

**Publication bias:** Grey literature (reports, preprints, non-peer-reviewed conference contributions) was not systematically included. Methodologically relevant approaches without peer-reviewed publication are not represented in the corpus.

**Recency bias:** The 2016–2026 timeframe excludes older but methodologically relevant work (e.g., early CIG formalisms, classical expert systems). These are considered as contextual literature in the paper but do not enter the systematic corpus.

**Search string design:** Block A operationalises the inference mechanism concept through paradigm-representative method terms (Approach C). Methods not described using these terms in the title or abstract will not be retrieved through database searching. Structured citation tracing (Section 6.5) addresses this recall loss.

**Single screener:** Primary screening is performed by one reviewer; the second reviewer participates in the consensus process but does not screen independently. The resulting recall risk is partially mitigated by the AI-assisted parallel screening protocol (Section 6.6), which provides an independent screening signal; AI-flagged disagreements are carried forward to full-text review regardless of human Phase 1 decision.

**AI-assisted screening:** AI-assisted parallel screening (Section 6.6) introduces risks of LLM-inherent bias and prompt sensitivity; the complete prompt is published as supplementary material. The AI screener has no autonomous exclusion authority; all final decisions remain with the human reviewer.

---

## 11. Deviations from Protocol

All deviations following protocol submission will be declared in the manuscript's "Limitations" section, with date and justification.

---

## 12. Version History

| Version | Date       | Changes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2.0     | 2026-06-29 | AI model specifications added: Claude Opus 4.8 for Phase 1 screening; Claude Sonnet 4.6 disclosed as protocol development assistant.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 2.0     | 2026-06-29 | AI-assisted parallel screening added: new Section 6.6 (methodology, model documentation, prompt design, agreement analysis, rationale + references). Sections 6.1, 6.2, 10 updated accordingly.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 2.0     | 2026-06-29 | Protocol completed: Sections 5.2–12 finalised. Search strategy and concept blocks confirmed (Block A: n=196 WoS hits, 2026-06-29). Sections 6–10 written (screening procedure, data charting, quality assessment, synthesis method, limitations). Sections 5.5–5.8 omitted by design. Full document translated to English. Converted to scoping review design: PRISMA-ScR (Tricco et al., 2018); Section 1 ScR rationale added, Section 7 terminology changed to data charting, Section 8 simplified per PRISMA-ScR Item 18, quality assessment limitation removed from Section 10. Section 3 converted from PICOC to PCC framework (Population, Concept, Context) per JBI/PRISMA-ScR methodology. Working title set. |

---

## References

1. Arksey H, O'Malley L. Scoping studies: towards a methodological framework. *Int J Soc Res Methodol*. 2005;8(1):19–32. doi:[10.1080/1364557032000119616](https://doi.org/10.1080/1364557032000119616)

2. Tricco AC, Lillie E, Zarin W, O'Brien KK, Colquhoun H, Levac D, et al. PRISMA Extension for Scoping Reviews (PRISMA-ScR): Checklist and Explanation. *Ann Intern Med*. 2018;169(7):467–473. doi:[10.7326/M18-0850](https://doi.org/10.7326/M18-0850)

3. Khraisha Q, Put S, Kappenberg J, Warraitch A, Hadfield K. Can large language models replace humans in systematic reviews? Evaluating GPT-4's efficacy in screening and extracting data from peer-reviewed and grey literature in multiple languages. *Res Synth Methods*. 2024;15(4):616–626. doi:[10.1002/jrsm.1715](https://doi.org/10.1002/jrsm.1715). PMID: 38484744.

4. Ghossein J, Hryciw BN, Ramsay T, Kyeremanteng K. The AI Reviewer: Evaluating AI's Role in Citation Screening for Streamlined Systematic Reviews. *JMIR Form Res*. 2025;9:e58366. doi:[10.2196/58366](https://doi.org/10.2196/58366). PMID: 40153601. PMCID: PMC11970706.
