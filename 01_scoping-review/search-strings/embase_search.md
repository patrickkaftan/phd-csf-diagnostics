# Embase – Search String & Hit Count

**Database:** Embase
**Interface/Syntax:** :ti,ab (title, abstract)
**Date executed:** 2026-08-04
**Hit count:** 171
**Protocol version:** SLR_Protocol_Pub1_v2.1.md, Section 5.4

## Search String (as executed)

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
  OR 'clinical pathway*':ti,ab
)
AND
(
  'guideline*':ti,ab OR 'electronic health record*':ti,ab
  OR 'electronic medical record*':ti,ab OR 'EHR':ti,ab OR 'clinical data':ti,ab
)
AND [2016-2026]/py
```

## Notes

- String executed verbatim from protocol v2.1 (Section 5.4), no interface-specific adaptation required.
- Export: RIS, imported into Zotero for deduplication (Section 6.3).
