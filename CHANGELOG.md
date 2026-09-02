# Changelog

## 2026-09-02

- Marked the notebook's `Run` section collapsed by default without changing
  executable code, then updated the shared Colab file in place.
- Replaced GitHub PDF-preview links with explicit authenticated downloads and
  added a compact `docs/README.md` document index.
- Rechecked all 14 PDF pages, embedded PDF links, notebook structure, validation
  tables, public video URLs, and saved Drive deliverables.
- Corrected stale README and `AGENTS.md` next-action text that still described
  Batch 1 as pending even though all four runs are complete.
- Added a prominent GitHub **Open in Colab** button that routes to the verified
  shared Drive notebook, avoiding the current private-repository importer issue.
- Created a compact review entrypoint in `PRESENTATION.md`.
- Added a one-page four-video validation summary.
- Rebuilt the six-page project guide so it uses the corrected true-scale
  Adaissah trajectory instead of the older misleading Kfar image.
- Replaced the example run's old trajectory page with the validated true-scale
  3D, top, and side views.
- Kept large GLB, video, and run artifacts in Google Drive and linked them from
  the repository rather than duplicating them in GitHub.

## 2026-08-31

- Audited the camera-center conversion against the official VGGT-Omega
  world-to-camera convention; no pose-direction or first-camera-origin defect
  was found.
- Replaced the misleading auto-scaled per-frame 3D chart with an orthographic
  true-proportion 3D view and equal-scale top and side views.
- Prevented static, interactive, and per-frame trajectory displays from drawing
  through retained-video cuts, unavailable poses, or translation-outlier edges.
  Raw poses remain exported without smoothing or deletion.
- Replayed the new display rules against all four saved validation trajectories.
  Adaissah's previous chart exaggerated lateral motion about 13x and vertical
  motion about 28x relative to forward motion; the new aspect removes that
  distortion. The known Kfar jump now creates a visible path break instead of a
  false interpolated connection.
- Parsed the edited notebook and all four changed Python cells successfully with
  zero syntax errors.
- Completed a fresh Adaissah T4 Colab run through the Results cell and visually
  verified the new true-scale 3D, top, and side trajectory views. Replayed the
  saved Kfar trajectory through the same logic and verified that its known
  translation outlier creates a path break.

## 2026-08-26

- Froze the clean baseline candidate with SHA256
  `C81F739C0550D1078448A697DEA238957D7BF996167A6C70E29D9F3EB1DBD15F`.
- Created exact local and Google Drive safety copies before further testing.
- Compared the clean local and executed shared notebooks at source-cell level.
- Promoted the clean notebook to the existing shared Colab file ID.
- Restored clean input defaults and retained the robust reusable-model memory guard.
- Recorded the complete baseline configuration in `configs/default.json`.
- Audited Run 2 warnings against the selected source frames. Confirmed the
  hard-bank/rapid-descent warnings as visible motion and identified one general
  cross-segment timing artifact.
- Changed motion diagnostics to use source-time gaps only inside the same
  retained segment and geometry component. Segment boundaries now break the
  displayed motion path without discarding geometrically connected poses.
- Statically parsed the modified reconstruction cell with zero syntax errors;
  a Colab regression run remains required before promoting this candidate to
  the shared canonical notebook.
- Uploaded the unexecuted timing-fix candidate as a separate Drive notebook,
  preserving the last validated shared notebook unchanged.
- Ran the timing-fix candidate on Kfar Tebnit and Majdal Zoun in Colab using
  true FP32 on a Tesla T4. Both completed without GPU fallback or degradation.
- Verified directly from saved Drive CSVs that retained-segment boundaries
  blank time/speed values, mark the incoming edge non-comparable, and break the
  displayed trajectory without splitting connected geometry.
- Recorded Batch 1 runs 3 and 4, including numerical and visual assessments.
  Batch 1 is now complete: four of four representative videos produced the
  required GLB, PNG, trajectory CSV, summary JSON, and packaged outputs.
- Promoted the clean validated timing-fix notebook to the existing shared
  canonical Drive file ID; the pre-validation safety copy remains the rollback.
- Froze a pre-organization snapshot, then simplified the canonical notebook
  without changing reconstruction logic: blank URL entry, collapsed optional
  settings, concise instructions, and important GLB/PNG/CSV/ZIP links first.
- Added visible selected-keyframe and trajectory images plus the quality-warning
  summary to the final Results screen.
- Verified the uploaded layout in Colab, executed the URL form, parsed the
  Results cell through its expected prerequisite guard, and restored the shared
  notebook as a clean zero-output file. New canonical SHA256:
  `4F5A85A9793A2C267FECF1838CA0239ECBB51EFF9B5165059A0ADE003BE466CD`.

## 2026-08-11

- Established a GitHub-based durable project-memory structure.
- Designated `FPV_Reconstruction.ipynb` as the single canonical notebook.
- Consolidated startup work into a collapsed Setup section.
- Added resilient sequential decoding and legitimate terminal EOF clamping.
- Prevented duplicate-frame substitution and fabricated per-frame trajectories after decode failure.
- Added raw and trusted XYZ exports and motion-sanity diagnostics.
- Defined a staged 8–12-video validation campaign.
