# FPV Reconstruction

This private repository is the durable project memory and versioned source for the FPV video reconstruction project.

Start with [`PROJECT_STATE.md`](PROJECT_STATE.md). Future Codex sessions should also read [`AGENTS.md`](AGENTS.md) before changing the project.

## Storage model

- GitHub: clean notebook, project state, decisions, configuration, validation tables, and reports.
- Google Drive: source videos and large run artifacts such as GLB, PLY, PNG, CSV, JSON, and executed notebooks.
- Chat: active collaboration, not the only source of project truth.

## Current objective

Validate one canonical Google Colab notebook across representative FPV videos before attempting metric scale or geographic alignment.

## Canonical notebook

[`notebooks/FPV_Reconstruction.ipynb`](notebooks/FPV_Reconstruction.ipynb)

The GitHub copy should remain free of execution outputs. Executed copies belong in Google Drive.

## Resume in a new Codex chat

Use this instruction:

> Read `AGENTS.md` and `PROJECT_STATE.md` completely, inspect the canonical notebook and validation files, verify current repository state instead of trusting stale assumptions, and continue from `Next action`.

