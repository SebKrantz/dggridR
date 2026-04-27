# Aggregate point data into grid cells

Bins a set of lon/lat points — optionally with associated numeric values
— into the cells of a discrete global grid. Returns a data frame (no
geometry) with per-cell statistics (equivalent to DGGRID's
`BIN_POINT_VALS` / `BIN_POINT_PRESENCE` operations).

## Usage

``` r
dgbin_points(
  dggs,
  lon,
  lat,
  values = NULL,
  output_count = is.null(values),
  output_mean = !is.null(values),
  output_total = FALSE
)
```

## Arguments

- dggs:

  A dggs object from
  [`dgconstruct`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md).

- lon:

  Numeric vector of longitudes (decimal degrees).

- lat:

  Numeric vector of latitudes (decimal degrees).

- values:

  Optional numeric vector of values to aggregate (same length as
  `lon`/`lat`). If `NULL`, only point counts are computed.

- output_count:

  Logical. Return count of points per cell. Default: `TRUE` when
  `values` is `NULL`, `FALSE` otherwise.

- output_mean:

  Logical. Return mean of values per cell. Only meaningful when `values`
  is supplied. Default: `TRUE` when `values` is not `NULL`.

- output_total:

  Logical. Return total (sum) of values per cell. Only meaningful when
  `values` is supplied. Default: `FALSE`.

## Value

A data frame with a `seqnum` column (cell ID) plus whichever of `count`,
`mean`, `total` were requested.

## Examples

``` r
library(dggridR)
data(dgquakes)
dggs <- dgconstruct(spacing=1000, metric=FALSE, resround='down')
#> Resolution: 3, Area (mi^2): 1173851.79791229, Spacing (mi): 843.496246531419, CLS (mi): 964.285490648183

# Count earthquakes per cell
dgbin_points(dggs, dgquakes$lon, dgquakes$lat) |> head(20)
#>    seqnum count
#> 1       1     1
#> 2       2   701
#> 3       4    35
#> 4       5   257
#> 5       7    68
#> 6       8   190
#> 7      12    51
#> 8      13     3
#> 9      14    94
#> 10     16     2
#> 11     18   202
#> 12     21   195
#> 13     22   210
#> 14     24    89
#> 15     25    11
#> 16     27    49
#> 17     28   974
#> 18     30     8
#> 19     31    48
#> 20     33     1

# Aggregate magnitude per cell
dgbin_points(dggs, dgquakes$lon, dgquakes$lat, values=dgquakes$mag,
             output_count=TRUE, output_total=TRUE) |> head(20)
#>    seqnum count     mean   total
#> 1       1     1 3.400000    3.40
#> 2       2   701 3.674608 2575.90
#> 3       4    35 4.477143  156.70
#> 4       5   257 3.429572  881.40
#> 5       7    68 4.482353  304.80
#> 6       8   190 3.432105  652.10
#> 7      12    51 3.570588  182.10
#> 8      13     3 4.366667   13.10
#> 9      14    94 4.037234  379.50
#> 10     16     2 4.550000    9.10
#> 11     18   202 3.424950  691.84
#> 12     21   195 3.461385  674.97
#> 13     22   210 3.296667  692.30
#> 14     24    89 3.377640  300.61
#> 15     25    11 3.353636   36.89
#> 16     27    49 4.131429  202.44
#> 17     28   974 3.278070 3192.84
#> 18     30     8 3.500000   28.00
#> 19     31    48 4.577083  219.70
#> 20     33     1 4.100000    4.10
```
