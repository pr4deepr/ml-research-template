# Project Setup

> **How to use this file:**
> Open your AI coding tool and tell it: "Read setup.md and help me set up this project."
> It will walk you through these questions and populate the template files for you.
> You can also fill this in manually if you prefer.

---

## 1. Research Question

**What are you trying to answer? What does success look like?**

> Example: "Does adding synthetic data augmentation improve rare-class detection in our imbalanced dataset? Success = F1 on minority class > 0.6 with no regression on majority classes."

*This populates: CLAUDE.md (Question section), memory/project_key_learnings.md (The problem)*

**Your answer:**


---

## 2. Data

**What data do you have? Describe format, size, known issues, and effective sample size.**

> Example: "50,000 images (224x224, RGB) across 10 classes from 3 collection sites. Effective N = 3 sites for cross-site validation. Known issue: 40% class imbalance (class 7 is 2% of data). Format: PNG + CSV labels."

*This populates: CLAUDE.md (Quick Reference > Data), data/README.md, docs/methodology.md (Data Awareness)*

**Your answer:**


---

## 3. Compute

**What hardware do you have? GPU, RAM, time budget, any constraints?**

> Example: "1x RTX 4090 (24GB VRAM), 64GB RAM, Python 3.10 via conda. Can dedicate ~8 GPU-hours/day. OS: Linux."

*This populates: CLAUDE.md (Quick Reference > Compute), environment.yml*

**Your answer:**


---

## 4. Prior Work

**Is there an existing approach you're building on? Key papers? Known baselines?**

> Example: "Building on ResNet (He et al., 2016) and CutMix augmentation (Yun et al., 2019). Similar work exists on balanced datasets but not on our long-tail distribution. Baseline: ResNet-18 trained without augmentation."

*This populates: docs/architecture_decisions.md, docs/experiment_roadmap.md*

**Your answer:**


---

## 5. Desired Outcomes

**What's the deliverable? Paper, internal report, proof of concept? Any deadline?**

> Example: "Conference paper for ISBI 2027 (deadline: September 2026). Secondary: method release on GitHub."

*This populates: manuscript/paper_outline.md (Target venue), CLAUDE.md (Manuscript-Experiment Map)*

**Your answer:**


---

## 6. Approach

**Do you already have an approach in mind, or do you want suggestions?**

> If yes: describe your planned approach (model, training strategy, evaluation plan).
> If no: describe what you've considered or ruled out, and the AI will suggest 2-3 options with trade-offs.

*This populates: docs/architecture_decisions.md, experiments/configs/ (first baseline config), docs/methodology.md (Metrics)*

**Your answer:**


---

## Instructions for AI Assistant

After collecting the answers above, use them to populate the following template files:

### Files to populate

| File | What to fill in |
|------|----------------|
| `CLAUDE.md` | Question, project graph (initial phases), Quick Reference (compute, data), Manuscript-Experiment Map |
| `docs/methodology.md` | Primary/secondary/diagnostic metrics, evaluation protocol, data awareness (effective N, splits) |
| `docs/experiment_roadmap.md` | Tier 1/2/3 experiments based on approach and deliverable |
| `docs/architecture_decisions.md` | Initial approach with rationale, key parameters |
| `data/README.md` | Data provenance from answer #2 |
| `memory/user_role.md` | User background (ask if not provided above) |
| `memory/project_key_learnings.md` | "The problem" section from answer #1 |
| `experiments/configs/` | First baseline config YAML (if approach is known) |
| `environment.yml` | Add project-specific dependencies |

### If the user doesn't have an approach

Suggest 2-3 options with trade-offs based on their data, compute, and research question. For each option, describe:
- The approach in 2-3 sentences
- Why it fits their constraints
- Key risks or limitations
- Estimated compute cost

Let the user choose before populating the template.

### Identify project type

Based on the answers, identify which project type best fits (see README.md > Customization by Project Type) and adjust the template accordingly:
- **Supervised Learning** -- emphasis on stratified splits, class imbalance
- **Self-Supervised / Unsupervised** -- downstream probe as primary metric, proxy metric warning
- **Generative Models** -- FID/IS + human eval, cherry-picking warning
- **Fine-tuning / Transfer Learning** -- contamination checks, zero-shot baseline
- **Applied / Engineering** -- latency/throughput, may skip manuscript/

### Skills & tools check

Check if the user has useful skills or plugins installed. If not, suggest relevant ones:

**Phase 1: Project setup**
- Verify git is initialized
- Verify conda/pip environment exists
- Check for AI coding skills that could help (ask permission before installing)

**Phase 2: When experiments get complex**
Suggest dedicated experiment tracking (W&B, MLflow, TensorBoard) only when:
- More than ~10 experiment configs in experiments/configs/
- Multiple people running experiments
- Need to compare dozens of runs visually
- Long-running sweeps that benefit from live dashboards

Until then, EXPERIMENT_LOG.md + YAML configs are sufficient.
