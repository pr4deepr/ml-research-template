# Project Retrospective: Lessons Learned

> **[Project Name]** -- [One-line project description]
>
> Date: [YYYY-MM-DD]

This retrospective captures what worked, what didn't, and what to do differently.
Part A contains universal process lessons (pre-filled as a reference checklist).
Part B is for domain-specific technical lessons you discover during your project.

---

## Part A: Process & Workflow Lessons

These lessons apply to any ML/DL project regardless of domain. They are pre-filled as a reference. Fill in "What happened" for each to document your experience.

### 1. Know your hardware before designing experiments

**Rule:** Before designing experiments, document your compute (GPU VRAM, RAM, disk, wall-clock budget). Derive feasible configurations from these constraints, not the other way around.

**What happened in this project:** [Fill in]

---

### 2. Screen before committing to long runs

**Rule:** Never go directly from idea to full training. Run a short screen (10-30% of full epochs, 3-5 configs) first. Define what "promising" means before running.

**What happened in this project:** [Fill in]

---

### 3. Map every experiment to a deliverable

**Rule:** Before running an experiment, answer: "Which paper section or decision does this serve?" If the answer is unclear, don't run it.

**What happened in this project:** [Fill in]

---

### 4. Identify your real metric early and validate proxies

**Rule:** Don't assume your training objective correlates with your evaluation metric. Check it in the first screen. If they diverge, use in-training probes or early eval checkpoints.

**What happened in this project:** [Fill in]

---

### 5. Always include a baseline

**Rule:** Include random init / majority class / "doing nothing" in every evaluation. Report improvements as deltas from baseline, not absolute numbers.

**What happened in this project:** [Fill in]

---

### 6. Know your effective N

**Rule:** Identify your independent unit of observation. Use it for statistical tests and confidence intervals. Report both total observations and effective N.

**What happened in this project:** [Fill in]

---

### 7. Test eval code before trusting results

**Rule:** Unit test evaluation functions with known inputs and expected outputs before running real evaluations. Label ordering bugs, index mismatches, and metric implementation errors are common and invisible.

**What happened in this project:** [Fill in]

---

### 8. Read the original paper before reimplementing

**Rule:** List every architectural choice from the reference paper before implementing. Diff your implementation against it. Undocumented deviations from the reference are bugs until proven otherwise.

**What happened in this project:** [Fill in]

---

### 9. Experiment reliability: foreground, logging, incremental saves

**Rules:**
1. Run experiments in foreground with direct python path
2. Use Python `logging` module -- never custom stdout, never shell redirect
3. Save results after EACH experiment, not at the end of a script
4. Check GPU is clear before launching
5. Seed model init for fair comparison

**OS-specific notes:**
- Windows: `spawn` is the only multiprocessing start method; background processes can become zombies; custom stdout replacements crash on terminal disconnect
- Linux/Mac: `fork` shares copy-on-write memory; shell redirect buffering can hide progress

**What happened in this project:** [Fill in]

---

### 10. AI tools amplify but also inflate scope

**Rule:** Use AI for critique and review, but apply a human filter to scope. Brainstorming sessions can generate dozens of experiment ideas -- filter ruthlessly back to what serves the deliverable.

**Practices that help:**
- Navigation hub (CLAUDE.md) as single project entry point
- Cross-session memory (project_key_learnings.md)
- Clear context between tasks to prevent context pollution
- Separate exploration from execution (plan mode)

**What happened in this project:** [Fill in]

---

### Pre-flight Checklist

Use before starting any experiment. Skip any item explicitly with rationale documented in EXPERIMENT_LOG.md.

- [ ] Question written?
- [ ] Maps to a deliverable (paper section or decision)?
- [ ] Screening result justifies this run (or this IS the screen)?
- [ ] Baseline defined?
- [ ] Compute budget checked (VRAM, disk, wall-clock)?
- [ ] Eval code tested?
- [ ] Config saved to `experiments/configs/`?

---

## Part B: Technical/Scientific Lessons

Domain-specific lessons from this project. Fill these in as you discover them.

### [EXAMPLE -- replace with your findings]

**Scope:** computer vision / classification

**Finding:** Data augmentation that worked well on balanced benchmarks (CutMix, MixUp) actually hurt minority class recall on our imbalanced dataset. The augmentations blended rare-class features with majority-class features, making rare classes harder to distinguish.

**Takeaway:** Always evaluate augmentation strategies per-class, not just on aggregate metrics. Augmentations designed for balanced datasets can mask or degrade rare-class signal in imbalanced settings.

---

### 1. [Technical finding title]

**Scope:** [your domain]

**Finding:** [What you discovered]

**Takeaway:** [Generalizable insight]

---

### 2. [Technical finding title]

**Scope:** [your domain]

**Finding:** [What you discovered]

**Takeaway:** [Generalizable insight]
