---
name: hackathon-data
description: Layout, schema, joins and gotchas of the hackathon dataset. Read before writing any code that loads, joins or analyzes the data.
---

# Hackathon dataset

STATUS: UNPROFILED
(If this line still says UNPROFILED, stop and run `/profile-data <path>` before anything else.)

## Source
- Name / provider:
- Access method (local files, S3, API, platform UI):
- Usage restrictions (can it leave the machine? external APIs allowed?):

## Cohort
- Total patients:
- Groups / indications and n per group:
- Clinical endpoints available (OS, PFS, response, stage...):

## Modalities present
| Modality | Path | Format | Patients covered | Key fields |
|----------|------|--------|------------------|------------|
|          |      |        |                  |            |

## Joining across modalities
- Patient ID column per file:
- ID format differences and how to normalize them:
- Patients missing each modality:

## Loading snippets (tested)
```python
# filled in by /profile-data
```

## Gotchas
-

## Which skills to use per modality
- scRNA / snRNA: single-cell-rna-qc, scvi-tools
- Spatial (Visium etc.): spatial-transcriptomics, scvi-tools (DestVI)
- Bulk RNA: pydeseq2
- H&E / imaging: Owkin MCP for TCGA reference only
- Literature: pubmed
(Delete lines for modalities we don't have.)
