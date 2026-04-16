# Experiment Roadmap

Prioritized by impact on the deliverable (paper / product / decision).

## Tier 1: Must-do (blocking deliverable)

| Experiment | Deliverable | Status |
|-----------|-------------|--------|
| [e.g., Baseline model] | Results §1 | TODO |
| [e.g., Core method evaluation] | Results §2 | TODO |

## Tier 2: Should-do (strengthens significantly)

| Experiment | Deliverable | Status |
|-----------|-------------|--------|
| [e.g., Ablation study] | Results §3 | TODO |
| [e.g., Comparison to alternative method] | Results §4 | TODO |

## Tier 3: Nice-to-have (defer to revision)

| Experiment | Why deferred | Status |
|-----------|-------------|--------|
| [e.g., Scaling analysis] | Compute-heavy, not needed for first submission | Deferred |

## Rules

- One experiment at a time (unless screening multiple configs)
- Every experiment must serve a deliverable (paper section, decision, or this roadmap)
- Compare against the same baseline throughout
- Document negative results with root cause in EXPERIMENT_LOG.md
- Screen before committing to full runs (see methodology.md > Constraints)
