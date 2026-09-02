# FPV Reconstruction — Focused Handoff

Updated: 2026-09-02

## Durable project repository

Private GitHub repository:

`https://github.com/eyalkras/fpv-reconstruction`

Local repository package:

`C:\Users\Cyber_AI\Desktop\fpv-reconstruction`

The GitHub `main` branch is the durable source for project instructions, decisions, the clean canonical notebook, validation schemas, and compact reports. Google Drive remains the source for large videos and generated run artifacts.

Canonical clean-notebook SHA256 at repository initialization:

`1B8C422C47A89F8E42C578691B3E1717D60CADC45C1BBE167AF15CEE44456352`

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

`C:\Users\Cyber_AI\Desktop\fpv-reconstruction\notebooks\FPV_Reconstruction.ipynb`

Current local baseline-candidate SHA256:

`9E2E5E0632A001477EB8ACAC1347D52F5C22AF4334CA4215A2F36FF29A60DC90`

Current shared Colab SHA256 after the 2026-08-31 trajectory-visualization update:

`9E2E5E0632A001477EB8ACAC1347D52F5C22AF4334CA4215A2F36FF29A60DC90`

Executed Drive timing-fix validation copy (kept as evidence):

`https://colab.research.google.com/drive/1GuKUMiHjKmIqkxuQ8NaZrrE2qWm0DPOa`

Local pre-validation safety snapshot:

`safety_snapshots/FPV_Reconstruction_pre_baseline_validation_20260826.ipynb`

Local pre-organization safety snapshot:

`safety_snapshots/FPV_Reconstruction_pre_ux_cleanup_20260826.ipynb`

Shared Google Drive folder:

`FPV_Shared_Project`

Drive folder ID:

`1hjLHEvGNGkMPJsGO6KUvl-_BjREYjtta`

Shared Colab notebook ID:

`1TIZ76z9lq0SDqArLEEBL9D3V-mILEmNX`

Colab URL:

`https://colab.research.google.com/drive/1TIZ76z9lq0SDqArLEEBL9D3V-mILEmNX`

Drive pre-validation safety copy:

`https://colab.research.google.com/drive/18XSYSbQpyjU65A0Gyn91RMhrhNbBiyaJ`

On 2026-08-26 the clean local candidate replaced the shared file in place
after a source-cell comparison. The shared file now has 58 cells, no saved
execution outputs, clean default input values, and the robust reusable-model
memory guard. The previous executed shared state remains available in the
Drive safety copy above.

After that promotion, source review of Run 2 exposed one general diagnostic
defect: motion was divided by the compressed clean-timeline gap across a
retained-segment boundary. The local candidate now uses source time only for
comparable edges inside the same retained segment and geometry component. This
does not alter VGGT inference or discard connected poses. On 2026-08-26 it
passed fresh Colab runs on Kfar Tebnit and Majdal Zoun; both saved boundary rows
correctly blank motion values and break the path while preserving one connected
geometry component.

Verified shared-notebook structure on 2026-08-26:

- 58 cells total
- 54 code cells
- 4 Markdown cells
- Setup code collapsed
- Blank, prominent direct-URL input form
- Optional input settings collapsed
- Main GLB, PNG, CSV, and ZIP links shown first in Results
- Main reconstruction, interactive 3D, selected keyframes, and trajectory PNG visible
- Resilient end-of-video decoding (`TERMINAL_EOF_CLAMP`)
- Motion-sanity analysis present
- Shared canonical has no saved execution outputs

The shared canonical now contains the clean timing-fix source that passed the
Kfar Tebnit and Majdal Zoun Colab runs. The separate executed candidate remains
available as validation evidence; the shared file has the same stable file ID
and no saved execution outputs.

The final presentation cleanup changed only code cells 3, 4, and 57: the input
form, the optional-settings title/visibility, and the Results display order.
All preprocessing, VGGT inference, timing, trajectory, and saving cells are
unchanged from the four-video validated baseline. The uploaded notebook was
opened in Colab; the URL form executed correctly and the Results cell parsed
and reached its expected missing-prerequisites guard when run alone. The clean
zero-output copy was then restored in place.

On 2026-08-31, the trajectory output was corrected without changing VGGT
inference, preprocessing, keyframe selection, or raw pose export. The per-frame
result now shows a true-proportion orthographic 3D path plus equal-scale top and
side views. It never smooths direct VGGT poses, and it does not connect or
interpolate across retained-video cuts, unavailable poses, or warned
translation jumps. Offline replay against all four saved validation CSVs
confirmed that Adaissah's apparently scrambled path was mainly an axis-scaling
artifact, while the known Kfar discontinuity is now displayed as a path break.
The edited Python cells pass static syntax validation. A fresh Adaissah Colab
run completed through the Results cell and visually confirmed the true-scale
3D/top/side output. Kfar's saved trusted-trajectory CSV was replayed through
the same break rule and confirmed that its warned translation edge becomes a
disconnected run rather than a fabricated line or interpolation.

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

## Current validation status

- Batch 1 manifest: complete (four selected videos).
- Run 1, Adaissah howitzer: completed with warnings.
- Run 2, Namer APC near Khiam: completed with warnings.
- Run 3, Kfar Tebnit: completed with warnings, 40/40 trusted poses.
- Run 4, Majdal Zoun excavator: completed with warnings, 27/28 trusted poses.

## Next action

1. Present the packaged baseline, corrected example run, and four-video evidence.
2. Record reviewer feedback and convert it into a prioritized change list.
3. Defer metric scale and geographic alignment until after the baseline review.

## Instructions for a new Codex session

Tell Codex:

> Read `C:\Users\Cyber_AI\FPV_PROJECT_FOCUSED_HANDOFF.md` completely. Inspect the canonical local notebook and shared Drive notebook. Verify current files and outputs rather than trusting stale statements. Continue from `Next action`. Preserve one canonical notebook and update this handoff whenever a material decision, fix, test result, or path changes.
