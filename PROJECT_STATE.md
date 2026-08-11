# FPV Reconstruction — Focused Handoff

Updated: 2026-08-11

## Objective

Build one reliable, organized Google Colab notebook that accepts a direct FPV video URL and produces a defensible VGGT-based reconstruction. The important user-facing outputs are:

- 3D reconstruction (`.glb`)
- Reconstruction preview (`.png`)
- Per-frame relative camera trajectory (`X, Y, Z`)
- Trusted/filtered trajectory CSV
- Keyframe and frame-selection audit CSVs
- Quality, motion, runtime, and failure diagnostics

The later objective is metric scale and geographic alignment (`altitude, latitude, longitude`). The current relative XYZ values are not metres or GPS coordinates.

## Canonical notebook

Local clean copy:

`C:\Users\Cyber_AI\Desktop\FPV_Reconstruction.ipynb`

Shared Google Drive folder:

`FPV_Shared_Project`

Drive folder ID:

`1hjLHEvGNGkMPJsGO6KUvl-_BjREYjtta`

Shared Colab notebook ID:

`1TIZ76z9lq0SDqArLEEBL9D3V-mILEmNX`

Colab URL:

`https://colab.research.google.com/drive/1TIZ76z9lq0SDqArLEEBL9D3V-mILEmNX`

Verified shared-notebook structure on 2026-08-11:

- 58 cells total
- 54 code cells
- 4 Markdown cells
- Setup code collapsed
- Resilient end-of-video decoding (`TERMINAL_EOF_CLAMP`)
- Motion-sanity analysis present
- Drive copy contains saved execution outputs

The Drive notebook is larger than the local clean copy because it contains saved outputs. Cell count and important source features match the intended modern notebook.

## Important implementation decisions

- Maintain one canonical notebook rather than separate notebooks for easy and hard videos.
- Keep implementation cells collapsed and place important outputs in the final Results section.
- Use sequential video decoding and tolerate legitimate end-of-stream frame-count mismatches.
- Never fabricate duplicate frames or fake per-frame XYZ coordinates after a decode failure.
- Export both raw and trusted trajectories.
- Show relative translation speed, angular speed, trajectory warnings, and reconstruction status.
- Treat XYZ and derived speed as scale-free until metric scale is established.
- More keyframes are not automatically better. Test quality versus GPU cost with controlled experiments.

## Existing evidence

The main Drive project folder is `FPV_Drone_Project`, containing `notebooks`, `models`, `runs`, and `videos`.

Five earlier Stage 1 v5 run folders were found. The inspected completed output still used the older Stage 2 folder:

`stage2_vggt_omega_v1_2_2_stable_resume_true_fp32`

Its trusted trajectory contained 27 trusted poses, one geometry component, no translation/rotation warnings, and a smooth relative trajectory. This is useful baseline evidence but is not validation of the newest notebook.

## Dataset

Repository:

`https://github.com/itamarwe/fpv-drone-strikes-lebanon-dataset`

The repository catalog is the source for selecting validation videos and their stable download links.

## Current validation strategy

Do not run 8–12 similar videos blindly. Use a staged campaign.

### Batch 1: four representative videos

Select:

1. Clear/stable flight
2. Fast-motion flight
3. Blurry or heavily compressed flight
4. Difficult geometry, abrupt turn, or scene-transition flight

Use identical default notebook settings first.

### Required output from every run

- GLB
- Reconstruction PNG
- Raw trajectory CSV
- Trusted trajectory CSV
- Selected-frames/keyframes CSV
- Summary/pipeline JSON
- Motion-sanity diagnostics
- Runtime, GPU, and memory information
- Warning or failure reason

### Validation fields

Create one row per video with at least:

- Video ID, URL, category, duration, source FPS, and resolution
- Notebook/configuration identifier
- Frames requested, decoded, selected, and used
- Trusted-pose count and percentage
- Geometry-component count
- Translation and rotation discontinuities
- Relative-speed and angular-speed outliers
- GLB and PNG availability
- Runtime and peak GPU memory
- Visual reconstruction assessment
- Result: `PASS`, `QUESTIONABLE`, or `FAIL`
- Failure category and notes

### Controlled keyframe experiment

For only one or two representative videos, compare lower/default/higher keyframe counts. Measure reconstruction quality, trusted poses, continuity, runtime, and GPU memory. Do not select a higher count merely because the point cloud appears denser.

### Batch 2

After fixing any systematic problems found in Batch 1, validate on another four to eight unseen videos. Rerun only cases affected by code or threshold changes.

## Planned deliverables

- `validation_manifest.csv`
- `validation_results.csv`
- Concise validation report
- Recommended default settings
- Known failure modes and thresholds
- Evidence-based decision about whether the notebook is ready for metric scaling

## Compute and access boundaries

- Google Drive access allows inspection of saved CSV, JSON, PNG, GLB, and other artifacts; it does not provide a Colab GPU.
- Colab may require the user to complete sign-in, Drive authorization, Hugging Face authorization, CAPTCHA, or runtime confirmation.
- Do not request or store Gmail passwords.
- Do not coordinate account cycling to evade free GPU quotas.
- Legitimate alternatives include waiting for quota recovery, using an authorized available runtime, reducing compute, or using paid/cloud GPU capacity.
- The computer/browser must remain awake while an interactive Colab run is active.

## Next action

1. Build the four-video Batch 1 manifest from the GitHub catalog.
2. Record the exact canonical notebook/configuration identifier.
3. Run the videos sequentially when an authorized GPU is available.
4. Read the saved Drive artifacts and populate the validation results table.
5. Decide whether to fix the notebook or proceed to Batch 2.

## Instructions for a new Codex session

Tell Codex:

> Read `C:\Users\Cyber_AI\FPV_PROJECT_FOCUSED_HANDOFF.md` completely. Inspect the canonical local notebook and shared Drive notebook. Verify current files and outputs rather than trusting stale statements. Continue from `Next action`. Preserve one canonical notebook and update this handoff whenever a material decision, fix, test result, or path changes.

