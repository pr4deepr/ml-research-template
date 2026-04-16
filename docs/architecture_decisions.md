# Architecture Decisions

Every decision with evidence and status. Update when decisions are validated or changed.

## Decisions

| Choice | Value | Evidence | Status |
|--------|-------|----------|--------|
| [e.g., Model architecture] | [e.g., ResNet-18] | [e.g., Screen showed best acc/compute trade-off] | Testing |
| [e.g., Learning rate] | [e.g., 1e-3] | [e.g., LR sweep, best val loss at 1e-3] | Validated |
| [e.g., Data split strategy] | [e.g., leave-one-subject-out] | [e.g., Subjects are correlated, random split leaks] | Fixed |

Status meanings:
- **Fixed** -- structural constraint, not changing (e.g., data split strategy, hardware limits)
- **Validated** -- tested and confirmed by experiment
- **Testing** -- being evaluated in current or upcoming screen

## Key Analyses

[Document important analyses that inform decisions. Examples: data distribution properties, theoretical considerations, literature findings, compute trade-offs.]

## Known Limitations

[Things that are suboptimal but accepted, with reasons.]

## Dead Code

[Unused code that should be cleaned up. Track it here so it doesn't accumulate silently.]
