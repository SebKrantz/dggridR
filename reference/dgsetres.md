# Set the resolution of a dggs object

Set the resolution of a dggs object

## Usage

``` r
dgsetres(dggs, res)
```

## Arguments

- dggs:

  A dggs object from dgconstruct().

- res:

  Resolution. Must be in the range \[0,30\]. Larger values represent
  finer resolutions. Appropriate resolutions can be found with
  dg_closest_res_to_area(), dg_closest_res_to_spacing(), and
  dg_closest_res_to_cls(). Default is 9, which corresponds to a cell
  area of ~2600 sq km and a cell spacing of ~50 km. Default: 9.

## Value

Returns a dggs object which can be passed to other dggridR functions

## Examples

``` r
library(dggridR)
dgsetres(dgconstruct(res=20), 10)
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
#> [1] 10
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
