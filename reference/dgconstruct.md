# Construct a discrete global grid system (dggs) object

Construct a discrete global grid system (dggs) object

## Usage

``` r
dgconstruct(
  projection = "ISEA",
  aperture = 3,
  topology = "HEXAGON",
  aperture_type = "PURE",
  num_aperture_4_res = 0L,
  res = NA,
  precision = 7,
  area = NA,
  spacing = NA,
  cls = NA,
  resround = "nearest",
  metric = TRUE,
  show_info = TRUE,
  orient = "SPECIFIED",
  azimuth_deg = 0,
  pole_lat_deg = 58.28252559,
  pole_lon_deg = 11.25
)
```

## Arguments

- projection:

  Type of grid to use. Options are: ISEA and FULLER. Default: ISEA3H

- aperture:

  How finely subsequent resolution levels divide the grid. Options are:
  3, 4, 7 (HEXAGON only). Not all options work with all projections and
  topologies. Default: 3

- topology:

  Shape of cell. Options are: HEXAGON, DIAMOND, TRIANGLE. Default:
  HEXAGON

- aperture_type:

  Aperture sequence type. Options are: `"PURE"` (single aperture value),
  `"MIXED43"` (alternating aperture-4 and aperture-3, HEXAGON only).
  Default: `"PURE"`.

- num_aperture_4_res:

  For `aperture_type = "MIXED43"`: number of aperture-4 resolutions
  before switching to aperture-3. Must be in \[0, res\]. Default: 0.

- res:

  Resolution. Must be in the range \[0,30\]. Larger values represent
  finer resolutions. Appropriate resolutions can be found with
  dg_closest_res_to_area(), dg_closest_res_to_spacing(), and
  dg_closest_res_to_cls(). Default is 9, which corresponds to a cell
  area of ~2600 sq km and a cell spacing of ~50 km. Only one of res,
  area, length, or cls should be used.

- precision:

  Round output to this number of decimal places. Must be in the range
  \[0,30\]. Default: 7.

- area:

  The desired area of the grid's cells. Only one of res, area, length,
  or cls should be used.

- spacing:

  The desired spacing between the center of adjacent cells. Only one of
  res, area, length, or cls should be used.

- cls:

  The desired CLS of the cells. Only one of res, area, length, or cls
  should be used.

- resround:

  What direction to search in. Must be nearest, up, or down.

- metric:

  Whether input and output should be in metric (TRUE) or imperial
  (FALSE)

- show_info:

  Print the area, spacing, and CLS of the chosen resolution.

- orient:

  Grid orientation. Options are: `"SPECIFIED"` (use explicit pole and
  azimuth values) or `"RANDOM"` (random uniform orientation; use
  [`set.seed()`](https://rdrr.io/r/base/Random.html) before for
  reproducibility). Default: `"SPECIFIED"`.

- azimuth_deg:

  Rotation in degrees of grid about its pole, value in \[0,360\].
  Default=0.

- pole_lat_deg:

  Latitude in degrees of the pole, value in \[-90,90\].
  Default=58.28252559.

- pole_lon_deg:

  Longitude in degrees of the pole, value in \[-180,180\].
  Default=11.25.

## Value

Returns a dggs object which can be passed to other dggridR functions

## Examples

``` r
library(dggridR)
dggs <- dgconstruct(res=20)
str(dggs)
#> List of 12
#>  $ pole_lon_deg      : num 11.2
#>  $ pole_lat_deg      : num 58.3
#>  $ azimuth_deg       : num 0
#>  $ aperture          : num 3
#>  $ aperture_type     : chr "PURE"
#>  $ num_aperture_4_res: int 0
#>  $ isMixed43         : logi FALSE
#>  $ numAp4            : int 0
#>  $ res               : num 20
#>  $ topology          : chr "HEXAGON"
#>  $ projection        : chr "ISEA"
#>  $ precision         : num 7

dggs <- dgconstruct(area=5,metric=FALSE)
#> Resolution: 14, Area (mi^2): 6.62642775724281, Spacing (mi): 2.0040855349603, CLS (mi): 2.28965624454932

# Aperture-7 hexagonal grid (ISEA7H)
dggs7 <- dgconstruct(aperture=7, res=3)

# Mixed aperture grid (ISEA43H)
dggsM <- dgconstruct(aperture_type='MIXED43', num_aperture_4_res=2, res=5)

# Random orientation (reproducible with set.seed)
set.seed(42)
dggs_r <- dgconstruct(res=4, orient='RANDOM')
```
