# DySARNet: Densely Squeezed-and-Excited Attention-Gated Residual Network for Dysarthric Speech Recognition and Severity Estimation

[![Paper DOI](https://img.shields.io/badge/DOI-10.1007%2Fs11042--024--20053--w-blue)](https://doi.org/10.1007/s11042-024-20053-w)
[![Springer Link](https://img.shields.io/badge/Publisher-Multimedia%20Tools%20and%20Applications-success)](https://link.springer.com/article/10.1007/s11042-024-20053-w)
[![Preprint](https://img.shields.io/badge/Preprint-ResearchGate-orange)](https://www.researchgate.net/publication/370642281_Dysarnet_A_Densely_Squeezed-and-Excited_Attention-Gated_Residual_Deep_Learning_Model_for_Dysarthric_Speech_Recognition_and_Severity_Estimation)

DySARNet is a deep learning architecture and research workflow for **dysarthric speech recognition** and **dysarthria severity estimation**.
This repository provides the project notebooks, reproducibility guidance, and citation metadata needed to make replication and downstream research fast and practical.

## Authors and Affiliation

- **Dr. Francis Jesmar P. Montalbo**
  Batangas State University, Philippines

## Official Paper

- **Title:** *DySARNet: A Densely Squeezed-and-Excited Attention-Gated Residual Deep Learning Model for Dysarthric Speech Recognition and Severity Estimation*
- **Journal:** Multimedia Tools and Applications (Springer)
- **DOI:** https://doi.org/10.1007/s11042-024-20053-w
- **Article URL:** https://link.springer.com/article/10.1007/s11042-024-20053-w
- **Preprint URL:** https://www.researchgate.net/publication/370642281_Dysarnet_A_Densely_Squeezed-and-Excited_Attention-Gated_Residual_Deep_Learning_Model_for_Dysarthric_Speech_Recognition_and_Severity_Estimation

## Repository Contents

- `DySARNet.ipynb` — main model development and experimentation notebook.
- `DySARNet-Evaluator.ipynb` — evaluation, benchmarking, and analysis notebook.
- `REPRODUCIBILITY.md` — deterministic run guidance, environment setup, and experiment tracking.
- `CITATION.cff` — standardized citation metadata for GitHub, Zotero, and reference tools.
- `metadata.jsonld` — machine-readable scholarly metadata for SEO/semantic indexing/LLM discoverability.

## Quick Start

### 1) Clone and enter the repository

```bash
git clone <your-fork-or-this-repo-url>
cd dysarnet
```

### 2) Create a clean Python environment

```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
python -m pip install --upgrade pip
```

### 3) Install core dependencies

> If notebook cells include additional imports, install them as prompted during first run.

```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter ipykernel
# Install a deep learning backend used by the notebooks (choose one):
# pip install tensorflow
# OR
# pip install torch torchvision torchaudio
```

### 4) Launch notebooks

```bash
jupyter notebook
```

Open and run:
1. `DySARNet.ipynb`
2. `DySARNet-Evaluator.ipynb`

## Reproducibility and Productionization Notes

For rigorous replication and handoff, follow `REPRODUCIBILITY.md` exactly. The checklist includes:

- fixed random seeds and deterministic settings,
- environment capture and dependency pinning,
- data versioning and split persistence,
- experiment logging and artifact management,
- model validation/reporting conventions,
- deployment readiness checks.

## Suggested Workflow for New Researchers and Engineers

1. Start with the published paper and this README.
2. Re-run baseline notebooks end-to-end.
3. Freeze a fully pinned environment after a successful baseline run.
4. Introduce one controlled experiment change at a time.
5. Record all deltas and metrics in a structured experiment log.
6. Cite this work via DOI and `CITATION.cff`.

## Research Impact, Visibility, and Discovery

This repository is structured to improve:

- **Academic visibility:** clear DOI, article links, citation file.
- **Search discoverability:** keyword-rich documentation and scholarly metadata.
- **LLM discoverability:** concise, machine-readable metadata (`metadata.jsonld`) and explicit repository semantics.
- **Reusability:** stepwise setup + reproducibility checklist.

## Keywords

Dysarthric speech recognition, dysarthria severity estimation, clinical speech AI, assistive AI, biomedical signal processing, deep learning, residual networks, squeeze-and-excitation, attention gating, reproducible machine learning, healthcare AI.

## Citation

If you use this work, please cite the published article (DOI) and/or this repository metadata in `CITATION.cff`.

## Disclaimer

This repository is intended for research and educational use. For clinical or medical deployment, ensure proper validation, regulatory compliance, privacy protection, and human expert oversight.
