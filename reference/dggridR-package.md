# Discrete Global Grids for R

*dggridR* provides discrete global grids (DGGs) — spatial binning on the
surface of the Earth using equal-area hexagonal, triangular, or diamond
cells. Unlike rectangular grids, DGG cells have the same area regardless
of their location, making them ideal for spatial statistics, point
aggregation, and multi-scale analysis. The package wraps the DGGRID
v9.0b C++ engine via Rcpp.

**Grid Construction**

[`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)
— Build a DGG specification (projection, topology, aperture,
resolution)  
[`dgsetres()`](https://sebkrantz.github.io/dggridR/reference/dgsetres.md)
— Change the resolution of an existing DGG specification  
[`dgverify()`](https://sebkrantz.github.io/dggridR/reference/dgverify.md)
— Validate a DGG specification  

**Grid Information**

[`dginfo()`](https://sebkrantz.github.io/dggridR/reference/dginfo.md) —
Print a human-readable summary of a DGG specification  
[`dggetres()`](https://sebkrantz.github.io/dggridR/reference/dggetres.md)
— Return a table of cell counts, areas, and spacings for all
resolutions  
[`dgmaxcell()`](https://sebkrantz.github.io/dggridR/reference/dgmaxcell.md)
— Return the maximum cell ID at a given resolution  
[`dg_closest_res_to_area()`](https://sebkrantz.github.io/dggridR/reference/dg_closest_res_to_area.md)
— Select resolution by target cell area  
[`dg_closest_res_to_spacing()`](https://sebkrantz.github.io/dggridR/reference/dg_closest_res_to_spacing.md)
— Select resolution by target inter-cell spacing  
[`dg_closest_res_to_cls()`](https://sebkrantz.github.io/dggridR/reference/dg_closest_res_to_cls.md)
— Select resolution by target characteristic length scale  

**Grid Materialization**

[`dgearthgrid()`](https://sebkrantz.github.io/dggridR/reference/dgearthgrid.md)
— Generate the full global grid as an sf object  
[`dgcellstogrid()`](https://sebkrantz.github.io/dggridR/reference/dgcellstogrid.md)
— Generate grid cell boundaries for specified cell IDs  
[`dgrectgrid()`](https://sebkrantz.github.io/dggridR/reference/dgrectgrid.md)
— Generate a grid covering a lat/lon bounding box  
[`dgshptogrid()`](https://sebkrantz.github.io/dggridR/reference/dgshptogrid.md)
— Generate a grid covering a shapefile or sf polygon  

**Point Aggregation**

[`dgpoints_to_cells()`](https://sebkrantz.github.io/dggridR/reference/dgpoints_to_cells.md)
— Map lon/lat points to grid cells; returns an sf grid with optional
per-cell counts  
[`dgbin_points()`](https://sebkrantz.github.io/dggridR/reference/dgbin_points.md)
— Aggregate numeric values by cell; returns per-cell count, mean, and/or
total  

**Cell Relationships**

[`dgneighbors()`](https://sebkrantz.github.io/dggridR/reference/dgneighbors.md)
— Return adjacent cell IDs for each input cell (hexagonal grids)  
[`dgchildren()`](https://sebkrantz.github.io/dggridR/reference/dgchildren.md)
— Return child cell IDs at the next finer resolution  
[`dgparent()`](https://sebkrantz.github.io/dggridR/reference/dgparent.md)
— Return the parent cell ID at the next coarser resolution  

**Coordinate Conversion**

Thirty functions convert between the five cell address systems supported
by DGGRID, named `dgINPUT_to_OUTPUT`: **GEO** (geographic lon/lat),
**SEQNUM** (globally unique integer cell ID), **Q2DI** (quad-based
integer), **Q2DD** (quad-based double), and **PROJTRI** (projected
triangle). The most commonly used are:  

[`dgGEO_to_SEQNUM()`](https://sebkrantz.github.io/dggridR/reference/dgGEO_to_SEQNUM.md)
— Geographic coordinates to cell sequence number  
[`dgSEQNUM_to_GEO()`](https://sebkrantz.github.io/dggridR/reference/dgSEQNUM_to_GEO.md)
— Cell sequence number to geographic coordinates  

**Data**

[`dgquakes`](https://sebkrantz.github.io/dggridR/reference/dgquakes.md)
— Lat/lon locations of 1,000 earthquakes off Fiji (from the `datasets`
package)  
[`dg_shpfname_south_africa()`](https://sebkrantz.github.io/dggridR/reference/dg_shpfname_south_africa.md)
— Path to a bundled South Africa border shapefile  

## Details

The recommended default grid is **ISEA3H** (Icosahedral Snyder Equal
Area, aperture 3, hexagonal), constructed with
`dgconstruct(projection = "ISEA", topology = "HEXAGON", aperture = 3)`.
Every resolution contains exactly 12 pentagonal cells (area 5/6 of a
hexagon); in the default orientation these are placed at out-of-the-way
locations. Use `orient = "RANDOM"` in
[`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)
for a uniformly random icosahedral orientation.

Additional grid families supported: ISEA4H, ISEA7H, ISEA43H, FULLER3H,
FULLER4H, FULLER7H, FULLER43H, ISEA4T / FULLER4T (triangular), and
ISEA4D / FULLER4D (diamond).

The package uses the DGGRID v9.0b C++ engine developed by Kevin Sahr,
accessed via a hand-written Rcpp bridge. The underlying DGGRID library
is available at <https://github.com/sahrk/DGGRID>.

## References

Sahr, K., White, D., & Kimerling, A. J. (2003). Geodesic discrete global
grid systems. *Cartography and Geographic Information Science*, *30*(2),
121–134.
[doi:10.1559/152304003100011090](https://doi.org/10.1559/152304003100011090)

Kimerling, A. J., Sahr, K., White, D., & Song, L. (1999). Comparing
geometrical properties of global grids. *Cartography and Geographic
Information Science*, *26*(4), 271–288.
[doi:10.1559/152304099782294186](https://doi.org/10.1559/152304099782294186)

Snyder, J. P. (1992). An equal-area map projection for polyhedral
globes. *Cartographica*, *29*(1), 10–21.
[doi:10.3138/27H7-8K88-4882-1752](https://doi.org/10.3138/27H7-8K88-4882-1752)

Gregory, M. J., Kimerling, A. J., White, D., & Sahr, K. (2008). A
comparison of intercell metrics on discrete global grid systems.
*Computers, Environment and Urban Systems*, *32*(3), 188–203.
[doi:10.1016/j.compenvurbsys.2008.02.002](https://doi.org/10.1016/j.compenvurbsys.2008.02.002)

## Author

Richard Barnes <rijard.barnes@gmail.com>, Kevin Sahr <sahrk@sou.edu>,
and Sebastian Krantz <sebastian.krantz@graduateinstitute.ch>
