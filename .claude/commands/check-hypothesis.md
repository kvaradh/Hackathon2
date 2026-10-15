---
description: Stress-test one candidate hypothesis against the data and the literature
argument-hint: <hypothesis statement or id>
---

Check this hypothesis: $ARGUMENTS

1. Restate it as one testable claim: which genes, cell types or features, in which group, compared with what.
2. Data check: list the Findings that support it and the ones that conflict. Report n per group. Flag it if any supporting result rests on fewer than 5 patients or on a single modality.
3. Literature check: search PubMed with gene names, cell types and cancer type only. Never send patient-level data. Return up to 5 PMIDs, each labeled supports / contradicts / related, with one line on why.
4. Critique: name the strongest alternative explanation (batch, purity, sampling site, subtype imbalance) and say what analysis would rule it out.
5. Verdict: novelty (known / partly known / new), evidence strength (low / medium / high), and a suggested rank_score from 0 to 1 with a one-line justification.

Return the result in the Hypothesis schema from CLAUDE.md, filling the literature and resolution_note fields.
