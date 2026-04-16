# Methodology

Single source of truth for evaluation rules, experiment execution practices, and constraints.

## Principles

1. **Never use proxy metrics as primary metric** -- training loss, reconstruction error, or other optimization objectives often do not correlate with downstream task performance. Always validate.
2. **Always include a baseline** -- random init, majority class, or "doing nothing." Without it, you cannot tell if your method helps.
3. **Statistical claims need confidence intervals** -- report mean [CI_low, CI_high], not point estimates. Bootstrap resample over independent units.
4. **Test eval code before trusting results** -- if the evaluation has a bug, every decision downstream is wrong.

## Metrics

| Metric | Role | Target | Compute cost |
|--------|------|--------|-------------|
| [Primary metric] | Primary | [Target value] | [Time estimate] |
| [Secondary metric] | Secondary | [Target value] | [Time estimate] |
| [Diagnostic metric] | Diagnostic | [Target value] | [Time estimate] |

Role definitions:
- **Primary** -- the metric you report in the paper and make decisions from
- **Secondary** -- supports the primary, adds nuance
- **Diagnostic** -- helps debug problems but isn't reported as a result

## Evaluation Protocol

### Screening
- Run short experiments first (10-30% of full training epochs)
- Define what "promising" means BEFORE running the screen (e.g., "> baseline + 2pp")
- Screen 3-5 configurations per question
- Mid-screen checkpoints to catch early failures

### Full evaluation
- Epochs: [full training length]
- Data split: [train/val/test strategy]
- Baselines: [always included in every eval]
- Confidence intervals: [bootstrap method, N resamples, resample unit]

### Shared evaluation code
- **File:** `evaluation/[eval_module].py`
- All experiment scripts import from this module -- never duplicate eval logic
- [List key functions and what they compute]

### Test coverage
- [List test files and what they verify]
- Minimum: one test per metric function with known input/output

## Experiment Execution Practices

1. **Run in foreground** -- background processes can become orphaned (especially on Windows). Use direct python path.
2. **Use proper logging** -- Python `logging` module, not print statements or shell redirect. Custom stdout replacements can crash when terminal disconnects.
3. **Save incrementally** -- save results per experiment or per epoch, not at the end of a script. On crash, you lose only the current run, not everything.
4. **Seed everything** -- document seed, framework version, environment name. Seed model init for fair comparisons between configurations.
5. **Check compute budget before starting** -- estimate VRAM, disk space, and wall-clock time. Verify GPU is clear before launching.

## Data Awareness

- **Report effective N** -- independent samples != correlated observations. A time-series of 70 frames from one subject is 1 independent sample, not 70.
- **Document class distribution** -- note any imbalance and how it's handled (oversampling, weighted loss, balanced accuracy).
- **Cross-validation must respect data structure** -- if samples from the same subject are correlated, use leave-one-subject-out, not random k-fold.

## Constraints

These are hard defaults. Override any constraint explicitly by writing your rationale in the EXPERIMENT_LOG.md entry.

1. **Every experiment must have a clear question written before running** -- "What does this test?" should have a one-sentence answer.
2. **Every experiment must map to a deliverable** -- a paper section, a decision, or a roadmap item. If it doesn't serve one, don't run it.
3. **No full training run without a screening result that justifies it** -- screens are cheap; wasted full runs are not.
4. **Negative results must be documented with root cause** -- "it didn't work" is not documentation. Why didn't it work?
5. **Eval code must have at least one test before trusting results** -- test with known inputs and expected outputs.
