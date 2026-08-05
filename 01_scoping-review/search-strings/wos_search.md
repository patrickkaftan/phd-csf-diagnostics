# Web of Science Core Collection – Search String & Hit Count

**Database:** Web of Science Core Collection
**Interface/Syntax:** TS= (Topic search: title, abstract, author keywords, Keywords Plus)
**Date executed:** 2026-08-04
**Hit count:** 205
**Protocol version:** SLR_Protocol_Pub1_v2.1.md, Section 5.4

## Search String (as executed)

```
TS=("knowledge graph*" OR "computer-interpretable guideline*"
    OR "bayesian network*" OR "random field*" OR "markov model*"
    OR "causal model*" OR "directed acyclic graph*"
    OR "graph neural network*" OR "graph embedding*"
    OR "neuro-symbolic" OR "probabilistic graphical model*")
AND
TS=("decision support" OR "CDSS" OR "clinical pathway*")
AND
TS=("guideline*" OR "electronic health record*" OR "electronic medical record*"
    OR "EHR" OR "clinical data")
AND PY=(2016-2026)
```

## Notes

- String executed verbatim from protocol v2.1 (Section 5.4), no interface-specific adaptation required.
- Export: RIS, imported into Zotero for deduplication (Section 6.3).
- Not to be confused with the earlier Block-A-only pilot hit count (n=196, documented 2026-06-29 during search string development): that figure tested Block A in isolation, not the final three-block query.
