# Validation Report

Status: awaiting Batch 1 runs.

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

