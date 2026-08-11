# Codex Project Instructions

Before taking project actions:

1. Read `PROJECT_STATE.md` completely.
2. Inspect the current repository and canonical notebook.
3. Check `DECISIONS.md`, `CHANGELOG.md`, and current validation files.
4. Verify paths, notebook structure, and saved outputs rather than trusting old chat statements.

Working rules:

- Maintain one canonical notebook: `notebooks/FPV_Reconstruction.ipynb`.
- Keep the GitHub notebook free of execution outputs.
- Do not commit videos, model weights, credentials, tokens, private keys, or large reconstruction artifacts.
- Store large run artifacts in Google Drive and record their Drive folder link in the validation results.
- Record the Git commit identifier and configuration for every validation run.
- Treat VGGT XYZ and translation speed as relative units until metric scale is established.
- Do not claim latitude, longitude, altitude, metres, or physical speed without explicit scale and geographic alignment evidence.
- Preserve the evidence-based `PASS`, `QUESTIONABLE`, or `FAIL` outcome; do not hide weak reconstructions.
- Update `PROJECT_STATE.md`, `DECISIONS.md`, and `CHANGELOG.md` after material decisions, fixes, or validated results.

## Next action

Build the four-video Batch 1 manifest from the linked public dataset, then run and score those videos with identical default settings.

