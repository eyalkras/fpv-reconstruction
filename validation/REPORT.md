# Validation Report

Status: Batch 1 complete. All four representative runs produced auditable outputs; the timing-fix candidate passed both fresh-video checks.

## Verified run 1 — Adaissah howitzer

- Run: `baseline_validation_20260811_r01`
- Result: `PASS_WITH_WARNINGS`
- Output folder: <https://drive.google.com/drive/folders/1mYRF8jyh3WjBN6N8kyG46DhMjD7qshsF>
- Candidate frames: 99; model frames: 25; trusted poses: 25/25.
- Geometry: one connected component; 750,000 exported points.
- Decode clamps: 0; translation outliers: 0; rotation outliers: 0.
- Relative translation speed: median 0.00857, maximum 0.02254 model units/s.
- Camera angular speed: median 2.096 deg/s, maximum 8.381 deg/s.
- Intrinsics focal-length coefficient of variation: 0.03444.
- Warning: one low-overlap edge at source time 15.44 seconds. Direct frame
  review shows a large but visually continuous forward approach; the adjacent
  VGGT pose steps are smooth, so the warning is retained without rejecting the
  pose.
- A separate retained-segment boundary occurs between source times 19.88 and
  25.76 seconds. The scene still overlaps strongly and remains one geometry
  component, but motion during the omitted 5.88 seconds is unobserved. The
  timing-fix candidate therefore breaks motion/interpolation at this boundary
  without splitting or discarding the reconstruction.
- Per-frame output: 602 retained frames; 25 direct Omega anchors, 547 labeled
  SE(3) interpolations, and 30 intentionally unavailable rows. The original
  per-frame logic already avoided interpolation across the retained-segment
  boundary; the fix makes the keyframe diagnostics and plots follow the same
  rule.
- Visual review: the point cloud forms a coherent single flight corridor and
  the camera path has no unexplained jumps. This is encouraging but one video
  is not sufficient to validate source-scene fidelity or hard-video behavior.

## Verified run 2 — Namer APC near Khiam

- Run: `baseline_validation_20260811_r02`
- Result: `PASS_WITH_WARNINGS`
- Output folder: <https://drive.google.com/drive/folders/1vqziNZ28jEiOEHSpPJ0u2T9k0311mLl3>
- Candidate frames: 108; model frames: 27; trusted poses: 27/27.
- Geometry: one connected component; 750,000 exported points.
- GPU: Tesla T4, true FP32, 6.487 GiB peak allocation; no frame fallback
  and no quality degradation.
- Relative translation speed: median 0.01807, maximum 0.34976 model
  units/s; 2 outlier edges.
- Camera angular speed: median 1.651 deg/s, maximum 45.132 deg/s;
  4 outlier edges.
- Intrinsics focal-length coefficient of variation: 0.05332.
- There are no input-continuity warnings and the reconstruction stays in one
  geometry component.
- Source/contact-sheet review on 2026-08-26 confirmed that the three remaining
  rotation warnings at source times 27.72, 28.72, and 30.44 seconds correspond
  to a visible hard bank/turn. The remaining translation warning at 21.04
  seconds occurs during a visible rapid descent/approach.
- One translation and one rotation warning at source time 35.52 seconds were
  artifacts of dividing an inter-segment pose step by a 0.04-second compressed
  clean-timeline gap even though 5.08 source seconds were omitted. The general
  fix keeps the geometrically connected reconstruction but makes motion edges
  non-comparable across retained-segment boundaries and breaks the displayed
  motion path there. Offline replay predicts corrected counts of 1 translation
  and 3 rotation warnings; a Colab rerun is still required to record new files.

## Defect found and fixed

A second run in the same T4 runtime failed the 10 GiB free-memory preflight
because the previous Omega model was intentionally still loaded. The guard now
permits a pinned, marked model-reuse candidate while retaining the strict
memory floor for a fresh load. This makes sequential validation runs possible
without silently reducing quality.

## Verified run 3 - Kfar Tebnit

- Run: `baseline_validation_20260826_r03_timing_fix`
- Result: `PASS_WITH_WARNINGS`
- Output folder: <https://drive.google.com/drive/folders/1LCuCx5kNE77sl4RA2IiSJU7yV_gy5wLE>
- Candidate/model/trusted poses: 159/40/40; one geometry component.
- Tesla T4 true FP32 peak allocation: 7.552 GiB; no fallback or degradation.
- One translation-speed outlier and no rotation outliers. Visual review shows the jump occurs during a large visible change from close buildings to a distant view, so it remains explicitly warned.
- The retained-segment boundary at model frame 34 is non-comparable: time gap and speed fields are empty and `path_break_before` is true, while connected geometry is preserved.
- GLB, PNG, trusted trajectory CSV, per-frame CSV, summaries, and ZIP are present.

## Verified run 4 - Majdal Zoun

- Run: `baseline_validation_20260826_r04_timing_fix`
- Result: `PASS_WITH_WARNINGS`
- Output folder: <https://drive.google.com/drive/folders/1FG-npX8MqhcK7O03mvFp5xifxCl96vU2>
- Candidate/model/trusted poses: 108/28/27; one geometry component.
- Tesla T4 true FP32 peak allocation: 6.568 GiB; no fallback or degradation.
- One translation-speed outlier, no rotation outliers, and one final pose masked as untrusted. The remaining trusted path and terrain reconstruction are visually coherent.
- The retained-segment boundary at model frame 25 is non-comparable: time gap and speed fields are empty and `path_break_before` is true.
- GLB, PNG, trusted trajectory CSV, per-frame CSV, summaries, and ZIP are present.

## Batch 1 conclusion

The candidate is a sound stable baseline for relative reconstruction: four of four runs completed, all retained one geometry component, and no run silently reduced GPU quality. Warnings are exposed rather than hidden. It is not yet evidence of metric distance or geolocation, and the Kfar large-jump case should remain in the regression set.

## Trajectory-display correction — 2026-08-31

The camera-center calculation was re-audited and kept unchanged. The apparent
Adaissah scrambling came mainly from independent axis stretching in the old
3D chart: its X and Y ranges are much smaller than its forward Z range. The
replacement uses true proportions, equal-scale top/side views, direct-pose
markers, and no smoothing. It also breaks the displayed path at retained cuts,
unavailable poses, and warned translation jumps while preserving every raw
pose in CSV.

A fresh Adaissah T4 run completed through Results and visually showed the
expected mostly-forward path. Replay of all four stored trajectories confirmed
that the rule is cross-video; Kfar's known extreme translation edge is not
connected or interpolated.

## Timing-fix offline replay

The candidate logic was replayed against both saved trusted-trajectory CSVs.
This verifies the boundary masks and robust-threshold arithmetic without
claiming a new VGGT inference run.

| Run | Comparable motion edges | Translation warnings | Rotation warnings | Path breaks |
| --- | ---: | ---: | ---: | ---: |
| Adaissah | 23 | 0 | 0 | 2 |
| Namer/Khiam | 25 | 1 | 3 | 2 |

Both added path breaks are retained-segment boundaries. Geometry remains one
connected component in each run. The candidate reconstruction cell also passed
static Python syntax parsing with zero errors. A fresh Colab execution remains
the required acceptance test.

## Batch 1 design

Select one video from each category:

1. Clear and stable
2. Fast motion
3. Blur or heavy compression
4. Difficult geometry, abrupt turn, or scene transition

Run identical default settings before performing any controlled keyframe-count comparison.

## Acceptance questions

- Did the requested frames decode without fabricated replacements?
- Is the reconstruction visually related to the source scene?
- Are trusted camera poses sufficiently complete and connected?
- Does the trajectory avoid unexplained translation or rotation jumps?
- Are GLB, PNG, CSV, and JSON outputs complete and readable?
- Does the notebook clearly reject or flag weak evidence?
