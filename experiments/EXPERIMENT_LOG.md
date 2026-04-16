# Experiment Log

All experiment results in one place. This is the single source of truth.
When metrics evolve, note which experiments used which metrics.

---

## [Experiment Name] ([Date]) -- [STATUS]

**Config:** `experiments/configs/[name].yaml`
**Reproducibility:** seed=[X], commit=[hash], env=[conda env name]
**Question:** [What this experiment answers -- one sentence]

| Config | Metric 1 | Metric 2 | Delta vs baseline | Notes |
|--------|----------|----------|-------------------|-------|
| baseline | X% | Y% | ref | |
| variant_a | X% | Y% | +Z% | |

**Findings:**
1. [Key finding with numbers]
2. [Key finding with numbers]

**Decision:** [What was decided based on these results]

---

## [Failed Experiment Name] ([Date]) -- NEGATIVE

**Config:** `experiments/configs/[name].yaml`
**Reproducibility:** seed=[X], commit=[hash], env=[name]
**Question:** [What this was supposed to answer]
**Hypothesis:** [What you expected]
**Result:** [What actually happened]
**Why it failed:** [Root cause -- not just "it didn't work"]
**What we learned:** [Insight that informs next steps]

---

For planned experiments, see [`docs/experiment_roadmap.md`](../docs/experiment_roadmap.md).
For experiment configs, see [`experiments/configs/`](configs/).
