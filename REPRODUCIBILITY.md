# Reproducibility and Deployment Readiness Guide for DySARNet

This document provides a practical, audit-friendly process for reproducing DySARNet results and preparing robust experiment pipelines.

## 1. Environment Standardization

- Use a dedicated environment (`venv` or `conda`) per project version.
- Record:
  - Python version
  - OS and hardware (CPU/GPU)
  - CUDA/cuDNN versions (if GPU)
  - Package versions (`pip freeze > requirements-lock.txt`)
- Prefer pinned dependencies for publication-grade reruns.

## 2. Deterministic Execution

Set all available random seeds before data splitting and training.

```python
import os
import random
import numpy as np

SEED = 42
os.environ['PYTHONHASHSEED'] = str(SEED)
random.seed(SEED)
np.random.seed(SEED)
```

If using framework backends:

- TensorFlow: set TF seed and deterministic ops where available.
- PyTorch: set torch/cuda seeds and deterministic backend options.

## 3. Data Governance

- Keep raw data immutable and read-only.
- Maintain a `data/README.md` (or equivalent) with:
  - source dataset name and version,
  - acquisition date,
  - preprocessing steps,
  - exclusion/inclusion criteria,
  - train/validation/test split method.
- Persist split indices to file so every rerun uses the same partitioning.

## 4. Experiment Tracking

For every run, log at minimum:

- run ID and timestamp,
- git commit hash,
- configuration (hyperparameters, augmentations, optimizer, scheduler),
- dataset/split identifier,
- final metrics (and confidence intervals if computed),
- model checkpoint path.

Minimal logging can be CSV/JSON; scalable logging can use tools like MLflow/W&B.

## 5. Evaluation Protocol

- Keep evaluation code separate from training where possible (`DySARNet-Evaluator.ipynb`).
- Report:
  - classification/regression metrics appropriate to each task,
  - per-class and aggregate metrics,
  - confusion matrix or equivalent error analysis,
  - robustness checks across seeds.
- Run at least 3 seeded reruns for stability reporting when feasible.

## 6. Artifact Management

Store and version:

- trained model weights,
- configuration files,
- preprocessing encoders/scalers,
- notebooks exported to HTML/PDF,
- evaluation plots/tables.

Recommended structure:

```text
artifacts/
  run-<timestamp>-<hash>/
    config.json
    metrics.json
    model.ckpt
    figures/
```

## 7. Production Readiness Checklist

Before deployment or external handoff:

- [ ] Environment lockfile exists and installs cleanly.
- [ ] Inference path tested on unseen samples.
- [ ] Data preprocessing is consistent between train and inference.
- [ ] Runtime and memory budget measured.
- [ ] Model versioning policy defined.
- [ ] Monitoring and drift-detection plan drafted.
- [ ] Risk controls documented (false positives/negatives implications).
- [ ] Human-in-the-loop review defined for safety-critical outcomes.

## 8. Reporting Template for New Experiments

Use this minimal template in issues, docs, or papers:

1. **Objective:**
2. **Dataset and split ID:**
3. **Model/config changes:**
4. **Training setup:**
5. **Primary metrics:**
6. **Error analysis:**
7. **Comparison vs baseline:**
8. **Limitations and next steps:**

## 9. Citation and Discoverability

- Cite DOI: https://doi.org/10.1007/s11042-024-20053-w
- Keep `CITATION.cff` current for repository-level citation tools.
- Keep metadata in `metadata.jsonld` synchronized with paper metadata.
