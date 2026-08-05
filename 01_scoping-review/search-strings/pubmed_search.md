# PubMed (MEDLINE) – Search String & Hit Count

**Database:** PubMed (MEDLINE)
**Interface/Syntax:** [Title/Abstract]
**Date executed:** 2026-08-04
**Hit count:** 159
**Protocol version:** SLR_Protocol_Pub1_v2.1.md, Section 5.4

## Search String (as executed)

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
  OR "clinical pathway*"[Title/Abstract]
)
AND
(
  "guideline*"[Title/Abstract] OR "electronic health record*"[Title/Abstract]
  OR "electronic medical record*"[Title/Abstract] OR "EHR"[Title/Abstract]
  OR "clinical data"[Title/Abstract]
)
AND ("2016/01/01"[Date - Publication] : "2026/12/31"[Date - Publication])
```

## Notes

- String executed verbatim from protocol v2.1 (Section 5.4), no interface-specific adaptation required.
- Export: RIS, imported into Zotero for deduplication (Section 6.3).
