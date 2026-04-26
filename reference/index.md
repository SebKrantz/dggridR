# Package index

## Grid Construction

Construct and configure a Discrete Global Grid System (dggs)
specification.

- [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)
  : Construct a discrete global grid system (dggs) object
- [`dgsetres()`](https://sebkrantz.github.io/dggridR/reference/dgsetres.md)
  : Set the resolution of a dggs object
- [`dgverify()`](https://sebkrantz.github.io/dggridR/reference/dgverify.md)
  : Verify that a dggs object has appropriate values

## Grid Information

Inspect a dggs object: print a summary, retrieve per-resolution
statistics, count cells, and automatically select a resolution from a
target area, spacing, or characteristic length scale.

- [`dginfo()`](https://sebkrantz.github.io/dggridR/reference/dginfo.md)
  : Print info about a dggs object to the screen
- [`dggetres()`](https://sebkrantz.github.io/dggridR/reference/dggetres.md)
  : Get table of grid resolution information
- [`dgmaxcell()`](https://sebkrantz.github.io/dggridR/reference/dgmaxcell.md)
  : Get largest cell id for a dggs
- [`dg_closest_res()`](https://sebkrantz.github.io/dggridR/reference/dg_closest_res.md)
  : Determine an appropriate grid resolution based on input data.
- [`dg_closest_res_to_area()`](https://sebkrantz.github.io/dggridR/reference/dg_closest_res_to_area.md)
  : Determine resolution based on desired area
- [`dg_closest_res_to_cls()`](https://sebkrantz.github.io/dggridR/reference/dg_closest_res_to_cls.md)
  : Determine an appropriate grid resolution based on a desired
  characteristic length scale of the cells.
- [`dg_closest_res_to_spacing()`](https://sebkrantz.github.io/dggridR/reference/dg_closest_res_to_spacing.md)
  : Determine grid resolution from desired spacing.

## Grid Materialization

Generate grid cell boundaries as sf geometries for plotting and spatial
analysis.

- [`dgearthgrid()`](https://sebkrantz.github.io/dggridR/reference/dgearthgrid.md)
  : Return the coordinates constituting the boundary of cells for the
  entire Earth
- [`dgcellstogrid()`](https://sebkrantz.github.io/dggridR/reference/dgcellstogrid.md)
  : Return boundary coordinates for specified cells
- [`dgrectgrid()`](https://sebkrantz.github.io/dggridR/reference/dgrectgrid.md)
  : Return the coordinates constituting the boundary of cells within a
  specified region
- [`dgshptogrid()`](https://sebkrantz.github.io/dggridR/reference/dgshptogrid.md)
  : Return boundary coordinates for cells intersecting a shapefile

## Point Aggregation

Aggregate lon/lat point data into grid cells.
[`dgpoints_to_cells()`](https://sebkrantz.github.io/dggridR/reference/dgpoints_to_cells.md)
returns an sf grid (optionally with per-cell counts);
[`dgbin_points()`](https://sebkrantz.github.io/dggridR/reference/dgbin_points.md)
returns a lightweight data frame of per-cell statistics.

- [`dgpoints_to_cells()`](https://sebkrantz.github.io/dggridR/reference/dgpoints_to_cells.md)
  : Return grid cells containing input points
- [`dgbin_points()`](https://sebkrantz.github.io/dggridR/reference/dgbin_points.md)
  : Aggregate point data into grid cells

## Cell Relationships

Query spatial relationships between cells.
[`dgneighbors()`](https://sebkrantz.github.io/dggridR/reference/dgneighbors.md)
finds adjacent hexagonal cells;
[`dgchildren()`](https://sebkrantz.github.io/dggridR/reference/dgchildren.md)
and
[`dgparent()`](https://sebkrantz.github.io/dggridR/reference/dgparent.md)
navigate the grid hierarchy across resolution levels.

- [`dgneighbors()`](https://sebkrantz.github.io/dggridR/reference/dgneighbors.md)
  : Return neighboring cell IDs for each input cell
- [`dgchildren()`](https://sebkrantz.github.io/dggridR/reference/dgchildren.md)
  : Return immediate child cell IDs for each input cell
- [`dgparent()`](https://sebkrantz.github.io/dggridR/reference/dgparent.md)
  : Return parent cell ID for each input cell

## Coordinate Conversion

Convert between the five cell address systems supported by DGGRID:
**GEO** (geographic lon/lat), **SEQNUM** (globally unique integer cell
ID), **Q2DI** (quad-based integer coordinates), **Q2DD** (quad-based
double coordinates), and **PROJTRI** (projected triangle coordinates).
Functions follow the naming convention `dgINPUT_to_OUTPUT`.
[`dgGEO_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_SEQNUM.md)
and
[`dgSEQNUM_to_GEO()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_GEO.md)
are the most commonly used.

- [`dgGEO_to_GEO()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_GEO.md)
  : Convert from GEO to GEO
- [`dgGEO_to_PLANE()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_PLANE.md)
  : Convert from GEO to PLANE
- [`dgGEO_to_PROJTRI()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_PROJTRI.md)
  : Convert from GEO to PROJTRI
- [`dgGEO_to_Q2DD()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_Q2DD.md)
  : Convert from GEO to Q2DD
- [`dgGEO_to_Q2DI()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_Q2DI.md)
  : Convert from GEO to Q2DI
- [`dgGEO_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_SEQNUM.md)
  : Convert from GEO to SEQNUM
- [`dgSEQNUM_to_GEO()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_GEO.md)
  : Convert from SEQNUM to GEO
- [`dgSEQNUM_to_PLANE()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_PLANE.md)
  : Convert from SEQNUM to PLANE
- [`dgSEQNUM_to_PROJTRI()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_PROJTRI.md)
  : Convert from SEQNUM to PROJTRI
- [`dgSEQNUM_to_Q2DD()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_Q2DD.md)
  : Convert from SEQNUM to Q2DD
- [`dgSEQNUM_to_Q2DI()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_Q2DI.md)
  : Convert from SEQNUM to Q2DI
- [`dgSEQNUM_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_SEQNUM.md)
  : Convert from SEQNUM to SEQNUM
- [`dgQ2DI_to_GEO()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DI_to_GEO.md)
  : Convert from Q2DI to GEO
- [`dgQ2DI_to_PLANE()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DI_to_PLANE.md)
  : Convert from Q2DI to PLANE
- [`dgQ2DI_to_PROJTRI()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DI_to_PROJTRI.md)
  : Convert from Q2DI to PROJTRI
- [`dgQ2DI_to_Q2DD()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DI_to_Q2DD.md)
  : Convert from Q2DI to Q2DD
- [`dgQ2DI_to_Q2DI()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DI_to_Q2DI.md)
  : Convert from Q2DI to Q2DI
- [`dgQ2DI_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DI_to_SEQNUM.md)
  : Convert from Q2DI to SEQNUM
- [`dgQ2DD_to_GEO()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DD_to_GEO.md)
  : Convert from Q2DD to GEO
- [`dgQ2DD_to_PLANE()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DD_to_PLANE.md)
  : Convert from Q2DD to PLANE
- [`dgQ2DD_to_PROJTRI()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DD_to_PROJTRI.md)
  : Convert from Q2DD to PROJTRI
- [`dgQ2DD_to_Q2DD()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DD_to_Q2DD.md)
  : Convert from Q2DD to Q2DD
- [`dgQ2DD_to_Q2DI()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DD_to_Q2DI.md)
  : Convert from Q2DD to Q2DI
- [`dgQ2DD_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgQ2DD_to_SEQNUM.md)
  : Convert from Q2DD to SEQNUM
- [`dgPROJTRI_to_GEO()`](https://sebkrantz.github.io/dggridR/reference/dgPROJTRI_to_GEO.md)
  : Convert from PROJTRI to GEO
- [`dgPROJTRI_to_PLANE()`](https://sebkrantz.github.io/dggridR/reference/dgPROJTRI_to_PLANE.md)
  : Convert from PROJTRI to PLANE
- [`dgPROJTRI_to_PROJTRI()`](https://sebkrantz.github.io/dggridR/reference/dgPROJTRI_to_PROJTRI.md)
  : Convert from PROJTRI to PROJTRI
- [`dgPROJTRI_to_Q2DD()`](https://sebkrantz.github.io/dggridR/reference/dgPROJTRI_to_Q2DD.md)
  : Convert from PROJTRI to Q2DD
- [`dgPROJTRI_to_Q2DI()`](https://sebkrantz.github.io/dggridR/reference/dgPROJTRI_to_Q2DI.md)
  : Convert from PROJTRI to Q2DI
- [`dgPROJTRI_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgPROJTRI_to_SEQNUM.md)
  : Convert from PROJTRI to SEQNUM

## Data

Example dataset and helper utilities bundled with the package.

- [`dgquakes`](https://sebkrantz.github.io/dggridR/reference/dgquakes.md)
  : All earthquakes with magnitude \>=3.0 earthquakes for 2015
- [`dg_shpfname_south_africa()`](https://sebkrantz.github.io/dggridR/reference/dg_shpfname_south_africa.md)
  : National border of South Africa
