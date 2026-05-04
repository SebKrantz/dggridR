# Changelog

## dggridR 4.1.0

- [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)
  gains `aperture = 7` for ISEA7H / FULLER7H hexagonal grids.
- [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)
  gains `aperture_type = "MIXED43"` with `num_aperture_4_res` for
  ISEA43H / FULLER43H mixed-aperture grids.
- [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)
  gains `orient = "RANDOM"` for a uniformly random icosahedral
  orientation (reproducible via
  [`set.seed()`](https://rdrr.io/r/base/Random.html)).
- New `dgneighbors(dggs, cells)` returns the adjacent cell IDs for each
  input cell (hexagonal grids only).
- New `dgchildren(dggs, cells)` returns the child cell IDs at the next
  finer resolution.
- New `dgparent(dggs, cells)` returns the parent cell ID at the next
  coarser resolution.
- New `dgpoints_to_cells(dggs, lon, lat)` maps lon/lat points to grid
  cells and returns an sf grid with optional per-cell counts.
- New `dgbin_points(dggs, lon, lat, values)` aggregates point data into
  grid cells, returning per-cell count, mean, and/or total as a data
  frame.
- [`dgearthgrid()`](https://sebkrantz.github.io/dggridR/reference/dgearthgrid.md)
  and
  [`dgcellstogrid()`](https://sebkrantz.github.io/dggridR/reference/dgcellstogrid.md)
  gain a `densify` parameter to insert extra vertices along cell edges
  for smoother boundaries.
- [`dgearthgrid()`](https://sebkrantz.github.io/dggridR/reference/dgearthgrid.md)
  and
  [`dgcellstogrid()`](https://sebkrantz.github.io/dggridR/reference/dgcellstogrid.md)
  now materialize sf polygon grids through a native C implementation
  using R’s C API, preserving DGGRID ring order and avoiding the
  previous s2/collapse polygon construction path. Illustrative
  conversion timings for full-earth grids improved from 3.854s to 0.150s
  at res 9 (~26x). This is achieved also via the *wk* package.
- pkgdown site added at <https://sebkrantz.github.io/dggridR/>.

## dggridR 4.0.0

- Updated bundled DGGRID C++ engine to v9.0b (upstream
  [SebKrantz/DGGRID](https://github.com/SebKrantz/DGGRID)).
- Re-architected `DgIDGGSBase::makeRF()` call for new v9.0b parameter
  order (`isApSeq`, `DgApSeq`, `hierNdxSysType`).
- `update_from_upstream.sh` rewritten for macOS compatibility
  (Perl-based text transforms) and updated to track SebKrantz/DGGRID.
- Fixed numeric precision issue on Apple Silicon introduced by DGGRID
  v9.0b.
- New DeepWiki AI documentation at
  <https://deepwiki.com/r-barnes/dggridR>.

## dggridR 3.1.1

CRAN release: 2026-01-20

- Bumped R dependency to 4.1.0 to fix CRAN issues.

## dggridR 3.1.0

CRAN release: 2024-07-26

- Fixed a numeric precision issue on Apple Silicon
  ([\#63](https://github.com/r-barnes/dggridR/issues/63)).
- Removed dplyr, rlang, and sp as dependencies; added collapse and s2
  (zero additional transitive dependencies), yielding significant
  performance gains especially in grid materialization.
- [`dgshptogrid()`](https://sebkrantz.github.io/dggridR/reference/dgshptogrid.md)
  now accepts an sf object in memory in addition to a shapefile path.
- [`dgcellstogrid()`](https://sebkrantz.github.io/dggridR/reference/dgcellstogrid.md),
  [`dgearthgrid()`](https://sebkrantz.github.io/dggridR/reference/dgearthgrid.md),
  [`dgrectgrid()`](https://sebkrantz.github.io/dggridR/reference/dgrectgrid.md),
  and
  [`dgshptogrid()`](https://sebkrantz.github.io/dggridR/reference/dgshptogrid.md)
  gain `return_sf = TRUE`; setting `return_sf = FALSE` returns a
  memory-efficient long data frame of cell-vertex coordinates.

## dggridR 3.0.0

CRAN release: 2023-01-18

- Fixes memory leaks in DGGRID.
- Switches from rgdal to the sf package.
- `dgtransform()` removed (previously deprecated); use
  [`dgGEO_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_SEQNUM.md)
  instead.

## dggridR 2.0.3

CRAN release: 2018-04-06

- Fixed bugs in
  [`dgshptogrid()`](https://sebkrantz.github.io/dggridR/reference/dgshptogrid.md)
  and
  [`dgrectgrid()`](https://sebkrantz.github.io/dggridR/reference/dgrectgrid.md)
  where `cellsize` was not respected.
- More informative warning messages.

## dggridR 2.0.0

- Complete restructuring of the internal C++ engine for improved speed
  and robustness across operating systems.
- Restructured engine directory layout to reduce compilation complexity.
- [`dg_shpfname_south_africa()`](https://sebkrantz.github.io/dggridR/reference/dg_shpfname_south_africa.md)
  converted from an object to a function.

## dggridR 1.0.0

- [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)
  gains `azimuth`, `pole_lat`, and `pole_lon` parameters.
- Added pentagon location map to the vignette.

## dggridR 0.1.0 and earlier

- Initial development releases: grid generation, shapefile support
  ([`dgshptogrid()`](https://sebkrantz.github.io/dggridR/reference/dgshptogrid.md)),
  debugging utilities, FLOSS licensing via Clipper, and various
  compiler-compatibility and CRAN-compliance fixes.
