# Return grid cells containing input points

Finds the grid cells that contain each of the supplied lon/lat points
and returns their boundaries as an sf data frame (equivalent to DGGRID's
`GENERATE_GRID_FROM_POINTS` operation). Duplicate points in the same
cell are deduplicated; only cells with at least one point are returned.

## Usage

``` r
dgpoints_to_cells(dggs, lon, lat, return_count = FALSE, ...)
```

## Arguments

- dggs:

  A dggs object from
  [`dgconstruct`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md).

- lon:

  Numeric vector of longitudes (decimal degrees).

- lat:

  Numeric vector of latitudes (decimal degrees).

- return_count:

  Logical. If `TRUE`, add a `count` column with the number of input
  points in each cell. Default: `FALSE`.

- ...:

  Further arguments passed to
  [`dgcellstogrid`](https://sebkrantz.github.io/dggridR/reference/dgcellstogrid.md).

## Value

An sf data frame of cell boundaries. If `return_count=TRUE`, includes a
`count` integer column.

## Examples

``` r
library(dggridR)
data(dgquakes)
dggs <- dgconstruct(spacing=1000, metric=FALSE, resround='down')
#> Resolution: 3, Area (mi^2): 1173851.79791229, Spacing (mi): 843.496246531419, CLS (mi): 964.285490648183
grid <- dgpoints_to_cells(dggs, dgquakes$lon, dgquakes$lat, return_count=TRUE)
```
