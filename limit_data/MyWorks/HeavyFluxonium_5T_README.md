# Heavy fluxonium: image-digitized axion sensitivity at 5 T

## Inputs and conventions
Source: dp_1v100_10mK_v2_2002_10653_nu20-30MHz.png, supplied by the user.
A = blue (upper), B = orange (lower), C = light blue (middle).
These are the same A/B/C configurations as in the previous light-fluxonium task.
Their qubit counts or detailed measurement protocols are not inferred from color.

This is a projected sensitivity, NOT an existing experimental exclusion.
The grey exclusion background and orange shaded region are not new curves.

B0 = 5 T; random-DP polarization power average = 1/3; equal DM densities;
uniform axial conversion field; common cavity transfer function; no change
in device or cavity performance with magnetic field.

g[GeV^-1] = epsilon * m[eV] * 1e9 / (sqrt(3) * 5 * 195.35).
The final data ALREADY include both 5 T and polarization correction.
Do not divide by 5 or sqrt(3) again. Do not strip the Bessel transfer factor.

## Files and units
HeavyFluxonium_5T_A/B/C.txt: whitespace-separated mass [eV], g [GeV^-1],
with comment lines starting '#'; suitable for numpy.loadtxt.
heavy_curve_A/B/C_5T.csv: the same mass and final coupling, plus frequency
[MHz], original epsilon, source-floor flag, and digitized pixel coordinates.
heavy_fluxonium_5T_all_curves.csv: combined table on the common mass grid.
HeavyFluxonium_5T_provenance.json: calibration, method and physical assumptions.

Each curve has 147 points, with mass approximately 8.29238e-8 to 1.23934e-7 eV
(approximately 20.05 to 29.97 MHz). No endpoint has been forced to exactly
20 or 30 MHz, and no clipping or extrapolation was used.
All clipped_at_source_floor values are zero. Unlike the previous light-data
image, these three visible curves have no unresolved cusp at the plot floor.
Do not reuse the previous light-curve clipping flag or add a resonance here.

Trace extraction uses one subpixel color-weighted center per fully visible
column (502 through 648). The orange line is distinguished from its fill.
The gentle slopes are retained; do not replace the lines by exact constants.
Axes are log-log, calibrated against visible ticks. One horizontal pixel
corresponds to about 0.276% in mass, and one vertical pixel to about 2.71%
in epsilon. These scales are not confidence intervals or accuracy guarantees.
The extra digits preserve numerical consistency, not simulation-level accuracy.

## Local notebook integration
Target: ~/works/AxionLimits/MySummaryPlots.ipynb.
Read AGENTS.md, git status, the actual notebook and its plotting helpers first.
Keep the existing light-fluxonium line, data, style and other local changes.
Save this as a DISTINCT heavy data set; never overwrite Fluxonium_5T_* files.
Choose the SAME A/B/C configuration as the currently plotted light curve when
identifiable. Otherwise use B provisionally and report that choice.
Use a separate HEAVY_FLUXONIUM_CURVE switch and add just one heavy projection
line with color='goldenrod', following existing normalization and conventions.
Inspect the current light implementation rather than guessing its helper names,
paths, unit conversions, style or active configuration.

The handoff document includes all numerical files and a checksum-verified
restoration script. No access to this conversation or its sandbox is needed.

## Reproducibility
Digitize again (requires numpy, pandas and Pillow):
  python digitize_heavy_fluxonium.py
Draw PNG/PDF/SVG from final TXT data (numpy and matplotlib):
  python plot_heavy_fluxonium.py
All original visible-column points are retained in these outputs.
