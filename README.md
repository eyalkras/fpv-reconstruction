# FPV Reconstruction

This public repository contains the finished relative-reconstruction baseline, its review material, and the durable project memory.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/eyalkras/fpv-reconstruction/blob/main/notebooks/FPV_Reconstruction.ipynb)

Use the button above to open the clean, verified notebook directly from this public repository. The same output-free source remains versioned at [`notebooks/FPV_Reconstruction.ipynb`](notebooks/FPV_Reconstruction.ipynb).

## Start here

For a short project review, open [`PRESENTATION.md`](PRESENTATION.md). GitHub's
inline PDF viewer currently may display an error; use the explicit **Download**
links below to open the original verified documents.

To run the notebook:

1. Sign in to Hugging Face and [accept the VGGT-Omega access conditions](https://huggingface.co/facebook/VGGT-Omega).
2. [Create a Hugging Face token](https://huggingface.co/settings/tokens) with **read** access.
3. Open the notebook with the **Open in Colab** button and select a **T4 GPU** or better.
4. In Colab, open **Secrets** using the key icon. Add the token with the exact name `HF_TOKEN`, paste the token as its value, and enable **Notebook access**.
5. Paste a direct video URL, choose **Runtime -> Run all**, and authorize Google Drive when requested.
6. Open **Results** for the GLB, PNGs, relative XYZ CSVs, diagnostics, and the complete ZIP. The files are also saved to Google Drive.

Never paste the token into a code cell or commit it to GitHub.

For project maintenance or a future Codex session, read [`PROJECT_STATE.md`](PROJECT_STATE.md) and [`AGENTS.md`](AGENTS.md) before changing files.

## Storage model

- GitHub: clean notebook, project state, decisions, configuration, validation tables, and reports.
- Google Drive: source videos and large run artifacts such as GLB, PLY, PNG, CSV, JSON, and executed notebooks.
- Chat: active collaboration, not the only source of project truth.

## Current objective

Present the validated relative-reconstruction baseline, collect reviewer feedback, and convert that feedback into a prioritized next-stage plan. Metric scale and geographic alignment remain outside the current baseline.

## Canonical notebook

[`notebooks/FPV_Reconstruction.ipynb`](notebooks/FPV_Reconstruction.ipynb)

The GitHub copy should remain free of execution outputs. Executed copies belong in Google Drive.

## Review material

Use these downloads instead of GitHub's inline PDF preview:

- [Download the project guide](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Project_Guide.pdf)
- [Download the example run](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Example_Run.pdf)
- [Download the validation summary](https://github.com/eyalkras/fpv-reconstruction/raw/refs/heads/main/docs/FPV_Validation_Summary.pdf)
- [Open the document index](docs/README.md)

## Resume in a new Codex chat

Use this instruction:

> Read `AGENTS.md` and `PROJECT_STATE.md` completely, inspect the canonical notebook and validation files, verify current repository state instead of trusting stale assumptions, and continue from `Next action`.
