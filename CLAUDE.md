# Multi-Agent Oncology Hypothesis Engine

## What we're building
Modality specialist agents analyze one data type each. An orchestrator collects their findings, resolves cross-modality conflicts, and outputs ranked, cross-checked hypotheses. NOT predictions: the cohort is too small for that.

## Dataset
Not confirmed yet. Read `.claude/skills/hackathon-data/SKILL.md` before touching any data.
If that file still says UNPROFILED, run `/profile-data <path>` first. Never guess file layouts.

## Architecture
- `agents/<modality>/` : one folder per specialist (only create folders for modalities that exist in the data)
- `orchestrator/` : conflict resolution and ranking
- `shared/schemas.py` : the contracts below; change them only with team agreement
- `demo/` : UI for judges

## Agent contract (every modality agent returns this)
```
Finding:
  modality: str
  claim: str                 # one testable sentence
  evidence: list[str]        # stats, plots, gene lists, file refs
  patients_supporting: list[str]
  n_patients: int
  effect_size: float | None
  confidence: low | medium | high
  caveats: list[str]         # batch effects, small n, missing data
```

## Hypothesis output (orchestrator returns this)
```
Hypothesis:
  statement: str
  supporting_findings: list[Finding]
  conflicting_findings: list[Finding]
  resolution_note: str       # how the conflict was handled
  literature: list[str]      # PMIDs from /check-hypothesis
  rank_score: float
```

## Rules
- Small n: always report n per group and stratify by indication/subtype when present.
- No patient-level data goes to external MCP servers. Send gene lists and queries only.
- Each person works in their own git worktree and branch.
- Prefer fast, simple methods first; upgrade only if time allows.
- When Claude makes a mistake twice, add a one-line rule here.
