# Annotation Prompts

LLM prompts used for semantic code annotation of the clinical guideline AWMF 030/141 v2 (2026).

## Approach

Guideline chapters converted to Markdown, then annotated with inline links to terminology concepts (ICD-10-GM, LOINC, OPS-301). Concept stubs generated with standardised YAML frontmatter (ev:// URIs, FHIR resource type, code system, annotation flags).

Architecture decision: Option B (FHIR-resource-oriented) —  
`condition/` (ICD-10-GM) · `observation/` (LOINC) · `procedure/` (OPS-301)

## Contents

- `guideline_annotation_prompt.md` — prompt for PDF → MD conversion + ICD/LOINC/OPS inline annotation
- `concept_stub_prompt.md` — prompt for generating YAML-frontmatter concept files from annotation output
