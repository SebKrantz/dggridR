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
head(grid)
#> Simple feature collection with 6 features and 2 fields
#> Geometry type: POLYGON
#> Dimension:     XY
#> Bounding box:  xmin: -175.3344 ymin: -26.61743 xmax: 179.5164 ymax: 54.95287
#> Geodetic CRS:  WGS 84
#>   seqnum                       geometry count
#> 1    231 POLYGON ((128.7576 -4.08531...   413
#> 2    250 POLYGON ((-162.1656 52.5833...   305
#> 3    254 POLYGON ((172.0247 -13.9241...   372
#> 4     62 POLYGON ((-6.675932 -6.3354...    48
#> 5     22 POLYGON ((-85.08052 49.7299...   210
#> 6    122 POLYGON ((129.5337 44.09063...   152
```
