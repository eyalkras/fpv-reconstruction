# Decisions

## One canonical notebook

Use one notebook for normal and difficult videos. Improve resilience inside that notebook rather than maintaining multiple situational versions.

## GitHub and Drive responsibilities

GitHub stores clean, reviewable source and compact evidence. Google Drive stores large videos and generated artifacts.

## Evidence before geolocation

Validate reconstruction geometry, camera-pose continuity, frame selection, motion sanity, and failure handling before metric scale or map alignment.

## Relative coordinates

VGGT camera translations have arbitrary reconstruction scale. Until scale is recovered, XYZ is not measured in metres and relative velocity is not physical speed.

## Staged validation

Test four deliberately different videos first. Fix systematic problems before spending GPU time on another four to eight unseen videos.

## Keyframe count

Do not assume more keyframes are better. Compare lower, default, and higher counts on only one or two videos while measuring quality, continuity, runtime, and GPU memory.

## Quality reporting

Every run receives `PASS`, `QUESTIONABLE`, or `FAIL`, with an explicit reason and links to evidence.

## Trajectory visualization

Camera trajectories must preserve the actual relative coordinate proportions. The
primary output shows an orthographic true-scale 3D path plus equal-scale top and
side views. Direct VGGT poses are never visually smoothed. Retained-video cuts,
unavailable poses, and translation-outlier edges remain in the raw CSV but are
not connected or interpolated in presentation paths.
