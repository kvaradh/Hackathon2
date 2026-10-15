---
description: Profile an unknown dataset and fill in the hackathon-data skill
argument-hint: <path-to-data>
---

Profile the dataset at: $ARGUMENTS

Work read-only. Do not modify, move or delete anything under that path.

1. Inventory: walk the directory tree. Report file count, total size, and extensions grouped by folder. Skip opening anything over 2 GB fully; sample it instead.
2. Identify modalities by format and content, for example:
   - .h5ad / .h5 / .mtx: single-cell or spatial counts
   - Space Ranger folders (spatial/, tissue_positions*): Visium
   - .svs / .ndpi / .tiff / .png tiles: H&E or other images
   - .vcf / .maf: variants (WES/WGS)
   - .csv / .tsv / .parquet / .xlsx: clinical or bulk tables
   Open a small sample of each to confirm. Do not trust the extension alone.
3. For each tabular file: shape, column names, dtypes, missingness per column, and 3 example rows with any patient identifiers truncated.
4. For each AnnData/count file: n_obs, n_vars, obs/var columns, layers, obsm keys, whether X looks raw or normalized.
5. Find the patient ID in every file. Work out how IDs differ across files (prefixes, sample vs patient suffixes) and write one normalize function that joins them. Then build a patients x modalities coverage table.
6. Clinical: list endpoints (survival, response, stage, subtype) and n per group.
7. Write a tested loading snippet for each modality and run it to confirm it works.
8. Look for usage restrictions in any README, LICENSE or data agreement file.

Then rewrite `.claude/skills/hackathon-data/SKILL.md`:
- Change STATUS to `PROFILED <today's date>`
- Fill every section with what you found
- Delete skill lines for modalities that are not present
- Add every surprise to Gotchas

Finish with a short summary: modalities found, n patients with all modalities, the three biggest gotchas, and which planned agents have no data to work on.
