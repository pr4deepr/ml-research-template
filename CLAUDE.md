# [Project Name]

> **First time?** Start with `setup.md` to set up this project, then fill in the sections below.
>
> **New session?** Read this file first, then `memory/project_key_learnings.md`
> for full narrative context. Check `experiments/EXPERIMENT_LOG.md` for latest results.

## Question
[One sentence: what are you trying to answer?]

**Answer so far:** [Update as results come in]

---

## Project Graph

```
[Draw your dependency graph here. Example:]

Data prep ──► Baseline model ── DONE
                  │
              Diagnostic: [what you found]
                  │
              Fix ──► Retrain ── DONE
                  │
              Eval ── DONE
                  │
         ┌────────┼────────┐
         ▼        ▼        ▼
      Screen 1  Screen 2  Screen 3
      RUNNING   pending   pending
         │
         ▼
      Best config ──► Final train ──► Manuscript
```

---

## Current Status

**[What's running right now, one line]**

---

## Navigation

| What | Where | Purpose |
|------|-------|---------|
| Project setup | [`setup.md`](setup.md) | Questionnaire for AI-assisted setup |
| All experiment results | [`experiments/EXPERIMENT_LOG.md`](experiments/EXPERIMENT_LOG.md) | Single source of truth for results |
| Experiment configs | [`experiments/configs/`](experiments/configs/) | YAML config per experiment |
| Evaluation methodology | [`docs/methodology.md`](docs/methodology.md) | Metrics, protocol, constraints |
| Architecture decisions | [`docs/architecture_decisions.md`](docs/architecture_decisions.md) | Every choice with evidence |
| Experiment roadmap | [`docs/experiment_roadmap.md`](docs/experiment_roadmap.md) | What to run and why |
| Critical assessment | [`docs/critical_assessment.md`](docs/critical_assessment.md) | Honest limitations and feedback |
| Manuscript outline | [`manuscript/paper_outline.md`](manuscript/paper_outline.md) | Paper structure and figures |
| External references | [`references/`](references/) | AI feedback, literature notes |
| Chronological record | [`CHANGELOG.md`](CHANGELOG.md) | What happened when |
| Project retrospective | [`docs/retrospective.md`](docs/retrospective.md) | Lessons learned, what to do differently |

---

## Manuscript ↔ Experiment Map

| Experiment | Paper section | Status |
|-----------|---------------|--------|
| [Experiment 1] | Results §X | TODO |
| [Experiment 2] | Results §Y | TODO |

---

## Quick Reference

> Fill this in at project start (via setup.md), not retroactively.

### Compute
- GPU: [e.g., 1x RTX 4090 24GB]
- RAM: [e.g., 64GB]
- Python: [e.g., /path/to/conda/envs/myenv/python]
- Time per screen experiment: [e.g., ~30 min]
- Time per full training run: [e.g., ~24h]

### Model config
- [Key hyperparameters]

### Data
- [Size, splits, class distribution]
- [Effective N vs reported N -- independent samples, not correlated repeats]

---

## Update Protocol

| Event | Update these files |
|-------|-------------------|
| New experiment result | EXPERIMENT_LOG.md, CLAUDE.md status + graph |
| Experiment fails (negative) | EXPERIMENT_LOG.md (negative entry), CLAUDE.md status |
| Architecture decision validated | architecture_decisions.md |
| Phase completes | CLAUDE.md graph, CHANGELOG.md, paper_outline.md checklist |
| Methodology change | docs/methodology.md |
| Eval bug discovered | methodology.md, EXPERIMENT_LOG.md (flag affected results), CHANGELOG.md |
| New finding for paper | CLAUDE.md manuscript map |
| Data changes | CLAUDE.md Quick Reference, methodology.md |
| External feedback received | critical_assessment.md, references/ |
| New experiment config | experiments/configs/ |
| New session starts | READ: CLAUDE.md, memory/project_key_learnings.md |

## Rules

See `docs/methodology.md` for evaluation rules and constraints. Key non-negotiables:
- Never use proxy metrics (e.g., training loss) as primary evaluation metric
- Always include a baseline (e.g., random init, majority class) in every evaluation
- Statistical claims need confidence intervals, not point estimates
- Every experiment must have a question and map to a deliverable
