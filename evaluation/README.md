# Evaluation

Shared evaluation code lives here. Create a module (e.g., `eval_metrics.py`)
as the single source of truth for all metrics. All experiment scripts import
from this module -- never duplicate eval logic.

## What belongs here

- Shared eval functions (metrics computation, data loading for eval)
- Eval tests (`test_*.py`) -- test the eval code itself with known inputs/outputs
- Screen scripts (`quick_screen_*.py`) -- lightweight experiment runners for screening

## Principle

**Test the eval, not just the model.** If the eval code has a bug,
every decision downstream is wrong. Write at least one test per metric
function with known input and expected output before using it for real evaluations.
