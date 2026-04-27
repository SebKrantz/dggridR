# Determine an appropriate grid resolution based on a desired characteristic length scale of the cells.

The characteristic length scale (CLS) is the diameter of a spherical cap
of the same area as a cell of the specified resolution.

## Usage

``` r
dg_closest_res_to_cls(
  dggs,
  cls,
  round = "nearest",
  show_info = TRUE,
  metric = TRUE
)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- cls:

  The desired CLS of the cells.

- round:

  What direction to search in. Must be nearest, up, or down.

- show_info:

  Print the area, spacing, and CLS of the chosen resolution.

- metric:

  Whether input and output should be in metric (TRUE) or imperial
  (FALSE)

## Value

A number representing the grid resolution

## Examples

``` r
library(dggridR)
dggs <- dgconstruct(res=20)
res  <- dg_closest_res_to_cls(dggs,1)
#> Resolution: 16, Area (km^2): 1.18491167242236, Spacing (km): 1.07508800966481, CLS (km): 1.22828188927244
dgsetres(dggs,res)
#> $pole_lon_deg
#> [1] 11.25
#> 
#> $pole_lat_deg
#> [1] 58.28253
#> 
#> $azimuth_deg
#> [1] 0
#> 
#> $aperture
#> [1] 3
#> 
#> $aperture_type
#> [1] "PURE"
#> 
#> $num_aperture_4_res
#> [1] 0
#> 
#> $isMixed43
#> [1] FALSE
#> 
#> $numAp4
#> [1] 0
#> 
#> $res
#> [1] 16
#> 
#> $topology
#> [1] "HEXAGON"
#> 
#> $projection
#> [1] "ISEA"
#> 
#> $precision
#> [1] 7
#> 
```
