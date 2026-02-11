# astro-carla

AKS (Adaptive Kernel Smoothing) and moment-map workflow for KCWI-style 3D datacubes.

## Main Notebook

- `aks_moments.ipynb`

The notebook supports:
- optional AKS generation from an input science cube (+ variance cube),
- per-structure moment map generation (`IM`, `cen`, `fwhm`, `nvox`) for `AKS` and `RAW`,
- spectra plotting by structure,
- per-structure 2x2 moment plots,
- final combined-field 2x2 plot.

## Data Layout

Expected structure:

- `KCWI/inputs/`
  - input FITS cubes (science + variance)
- `KCWI/runs/<dataset>/aks/<run_id>/`
  - AKS outputs (`AKS.fits`, `AKS.mask.fits`, `AKS.var.fits`, subcubes, metadata)
- `KCWI/runs/<dataset>/moments/<run_id>/`
  - moment FITS outputs per structure
- `KCWI/runs/<dataset>/plots/<run_id>/`
  - generated PDFs

## Configuration

In the first notebook cell:
- choose dataset in `dataset_configs`,
- set AKS params (`aks_params`),
- set dataset physics (`redshift`, `redshift_err`, `line_rest_aa`, `kcwi2cgs`, `disp2fwhm`),
- toggle `RUN_AKS`:
  - `True`: regenerate AKS outputs,
  - `False`: reuse existing AKS outputs and run downstream stages.

## Notes

- Spectral/spatial scales (`pix2angstrom`, `pix2asec`) are resolved from FITS headers.
- The final combined velocity panel uses dataset `z_sys` reference.
- Plot limits/ticks are benchmarked for consistency across structures.

