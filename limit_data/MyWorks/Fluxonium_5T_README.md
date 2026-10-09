# Light fluxonium axion-photon sensitivity (5 T)

`MySummaryPlots.ipynb` selects curve **B**, the source orange curve chosen
by the user on 2026-10-09 for both light and heavy fluxonium. The light line
is goldenrod, with the annotation `Light fluxonium (5 T)`;
`FLUXONIUM_CURVE` selects A, B, or C. Display-only vertical segments extend
both endpoints to the upper axis limit to show the scanned mass range.

The three TXT files contain `mass_eV g_agamma_GeV_inv` in two columns.
Their CSV sidecars contain the same values plus `clipped_at_source_floor`.
Run `python restore_fluxonium_5T.py <explicit staging directory>` to restore
and verify the original, byte-identical handoff data using only the standard
library. Checks cover checksums, row counts, finite positive values,
strictly increasing masses, TXT/CSV agreement, and clipping flags.

These curves were digitized from
`dp_1v100_10mK_v2_1810_11006_nu1500-2500MHz.png`, rather than exported from
the original simulation. All points and the source cavity/Bessel structure
are retained, with no smoothing, decimation, or extrapolation.

The conversion already applied is
`g[GeV^-1] = epsilon * mass[eV] * 1e9 / (sqrt(3) * 5 * 195.35)`.
Do not apply the 5 T or polarization correction again. The assumptions are
equal local DM densities, a uniform static conversion field parallel to
the cylinder axis/detected mode, and a shared cavity response. Effects of
the conversion field on device, cavity, noise, coherence, and readout
performance are neglected; this static field is distinct from flux-bias
frequency scanning.

A, B, and C have 387, 339, and 372 points, respectively. Curve B has three
source-floor connector points from the original epsilon = 1e-15 display
floor (about 5.6e-15 GeV^-1 after conversion). Those points do not establish
a resolved physical minimum and must retain their flags. Curve C has no
source-floor flags.

`Fluxonium_5T_provenance.json` is the checksum-verified historical handoff
snapshot, preserved unchanged. Curve B is now explicitly selected by the
user. Detailed qubit and measurement identities are not established by the
digitized data.
