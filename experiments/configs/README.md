# Experiment Configs

One YAML config per experiment run. These are version-controlled alongside results for reproducibility.

## Naming Convention

`[experiment_name].yaml` -- name should match the corresponding entry in EXPERIMENT_LOG.md.

Examples:
- `baseline_resnet18.yaml`
- `screen_learning_rate.yaml`
- `ablation_no_augmentation.yaml`

## What to Include

```yaml
# experiment: [name matching EXPERIMENT_LOG.md entry]
# date: YYYY-MM-DD
# question: [what this experiment answers]

model:
  name: [architecture]
  pretrained: [true/false]
  # [model-specific parameters]

training:
  epochs: [number]
  batch_size: [number]
  learning_rate: [number]
  optimizer: [name]
  seed: 42
  # [training-specific parameters]

data:
  split: [split file or strategy]
  augmentation: [description]
  # [data-specific parameters]

eval:
  metrics: [list of metrics]
  baseline: [what to compare against]
```

## Tips

- Keep configs flat and readable -- avoid deep nesting
- Include the seed in every config
- If a config is a variant of another, note what changed in a comment
- Configs are for recording what was run, not for driving code (though you can load them programmatically if you want)
