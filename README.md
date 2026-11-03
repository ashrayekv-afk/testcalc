# NKPI 9.1.5 — original natural-eye appearance, continuous corneal review

Release identifier: **9.1.5-original-natural-eye**

Complete GitHub upload package. This release restores the earlier natural-eye materials
and keeps the newer continuous corneal maps and C-value audit. It is a display update,
not a new model fit, an anatomical validation, or an optical/surgical planning tool.

## Upload these five files

Extract **NKPI_v915_GitHub_Upload.zip** once. Upload the extracted contents to the
repository root, replacing matching files:

```
kcn_dual_calculator_app.py
nkpi_runtime.zip
requirements.txt
README.md
.streamlit/config.toml
```

Keep **nkpi_runtime.zip zipped**. Upload it together with the matching launcher
`kcn_dual_calculator_app.py`. Keep `.streamlit/config.toml` inside the `.streamlit`
folder. Do not place all five items inside an extra enclosing folder.

Keep `kcn_dual_calculator_app.py` as the Streamlit main file. Python **3.12** remains
the target deployment version. Reboot the existing app, refresh, and check for
**9.1.5-original-natural-eye** in the footer. Import the original reports, confirm the
correct eyes/visits/measurements, and calculate. This update does not change the import
schema; report selection still needs to be restored after a fresh browser session.

The entrypoint verifies the runtime's SHA-256 and extracts the complete app internally.
An old launcher correctly rejects a new runtime; always upload both matching files.

## What changed

- The original procedural iris/pupil, smooth scleral shading and clear corneal-shell
  reflection now surround the current continuous surface. Natural eye is the default.
- The SAME base anatomy remains underneath thickness, anterior/posterior curvature,
  and anterior/posterior elevation maps. Map colors remain opaque and unlit.
- GPU depth handling keeps the shell, iris and globe in the correct visual order.
  No transparency highlights are added to quantitative map colors.
- No missing-tissue wedges were reintroduced. Slice through point keeps the intact
  eye, linked line, adjustable direction and separate profile underneath.
- Canvas fallback uses smooth normal-interpolated shell shading. WebGL context loss
  falls back without clearing the selected point or measurements.
- The Color label no longer breaks into separate lines at narrow desktop widths.

## Retained without measurement changes

OD/OS layout and shared controls; equal physical axis scale; continuous display-only
completion; all five selected-point readings; compatible shared map scales; source
support overlay; original-report access; both-eye PNG export; input verification;
NKPI scores and model/impact audit. No demo-eye selector or Observed change & evidence
panel was restored.

The surface-construction modules, map/completion modules, entire extractor, models,
and assessment logic are byte-for-byte identical to 9.1.4. The backend's only change is
its UI version string. Source coordinates and C are never adjusted to improve appearance.

## Verified C versus the reconstructed minimum

**Verified C** is the scalar thinnest-pachymetry input confirmed by the user for the
specific eye/visit, not an independent automated validation by this viewer.
**Reconstructed minimum** is the minimum supported by the original spatial model.
A report-image reconstruction can differ from C because of color bins, sample spacing,
occlusion and local fitting. Both numbers and their difference remain separate.

The marker uses verified reported thinnest XY when available and correctly linked.
Otherwise it starts at the original reconstructed minimum and says that C's exact
location was not supplied. C alone cannot provide an XY coordinate. Broad visual fills
do not change that selection or acquire precise numerical readings.

## Accuracy and continuity

No holes in the display does NOT mean complete measured data. The existing completion
rules produce a continuous viewing envelope; unknown regions remain identifiable with
Show data support, and broad completed areas have no fabricated numeric readings.
Entirely missing maps and unlinked eyes/visits stay unavailable.

Report-image geometry remains approximate. The inner boundary is thickness-derived
unless valid independent posterior coordinates were supplied. Iris appearance, globe
and unmeasured peripheral tissue remain reference anatomy. Equal x/y/z scaling prevents
intentional depth exaggeration but does not prove a 1:1 patient replica. This version
restores natural appearance, not unmeasured anatomical information or patient optics.

## Verification performed for this release

- 75 viewer browser checks, covering WebGL and Canvas, desktop/mobile, all map modes,
  rotation/zoom, source preservation, verified-C selection, visit isolation, source modal,
  slice direction, PNG export, WebGL loss/restoration and cleanup.
- 8 full-component smoke checks using the real component HTML/script order, real backend
  configuration and both-eye calculator responses. The Streamlit bridge was simulated.
- 41 Python tests and all retained JavaScript test suites, plus 8 new renderer checks.
- 24 eye-result comparisons versus 9.1.4 matched exactly, excluding UI-version text.
- Representative PDF generation passed basic byte/header/EOF checks (not visual review).
- Final ZIP, file manifest and hash-checked launcher extraction verified.

Browser tests use explicitly synthetic engineering data, not the latest patient pictured
in chat. Fresh end-to-end OCR, native-device anatomical accuracy and a live Streamlit
server/cloud deployment were NOT tested here. The local environment did not have
Streamlit installed and could not reach the package server. Dependencies are unchanged:
`streamlit==1.50.0`, `reportlab==4.4.9`, `numpy>=1.26.4,<3`. These are compatibility pins,
not a claim to use the newest published versions. Tests ran under Python 3.13; deployment
remains targeted at 3.12 as before. Software tests are not clinical validation.

Further details inside the runtime: `docs/NATURAL_EYE_RESTORE.md`,
`docs/CONTINUOUS_REVIEW.md`, `docs/V915_VERIFICATION.md`, `docs/NUMERICAL_IMPORT.md`.

## Privacy

No patient reports, photos, browser test cases or account credentials were added to this
distribution. Do not commit patient exports or secrets to GitHub. Use de-identified data
on public hosting and follow the institution's approved hosting/security arrangements.
Original-report access uses the already-linked browser data; no new remote asset service
was introduced. Existing third-party notices and OCR licenses are retained.
