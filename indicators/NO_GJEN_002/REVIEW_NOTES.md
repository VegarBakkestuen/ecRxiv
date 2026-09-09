# NO_GJEN_002 v0.1.0 — internal review notes

Prepared for internal NINA code review in September 2026.

## Scope of this revision

- Added Vegar Bakkestuen as an author.
- Updated metadata to semantic version `0.1.0` and retained status `incomplete`.
- Replaced workstation-specific repository paths with repository-local paths.
- Added environment variables for external NINA data roots:
  `NINA_P_PROJECTS_ROOT` and `NINA_R_DATA_ROOT`.
- Corrected aerial-image tensor dimensions and channel order in the Python
  inference example.
- Corrected command-line Boolean handling and CPU/GPU selection.
- Changed region and vegetation-zone assignment to use the largest spatial
  overlap instead of the count of intersecting features.
- Added input checks to the indicator scaling function.
- Aligned the ECT label in the text with metadata (`B3`).

## Items for the reviewer

1. Confirm that `B3 - Functional State Characteristics` is the intended ECT
   classification.
2. Confirm whether the 20th/80th input-image percentiles in histogram
   normalisation are methodologically intended.
3. Verify the inference example against the exact pinned revision and model
   checkpoints from Meta's High Resolution Canopy Height repository.
4. Verify that `vegHeights_skog_climZoneRegion.csv` is the authoritative forest
   reference table and document its provenance/version.
5. Confirm the intended treatment of polygons spanning region or vegetation-zone
   boundaries. This revision uses the class with the largest overlapping area.
6. Recalibrate aerial-image reference levels before changing status from
   `incomplete` or releasing version `1.0.0`.

## Validation status

- Quarto fence structure and Python syntax have been checked.
- Metadata values and workbook rendering have been checked.
- Full Quarto execution was not performed in the review workspace because R,
  Quarto, the model checkpoints and NINA's external forest-reference table were
  unavailable.
