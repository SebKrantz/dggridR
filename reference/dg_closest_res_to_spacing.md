# Determine grid resolution from desired spacing.

Determine an appropriate grid resolution based on a desired spacing
between the center of adjacent cells.

## Usage

``` r
dg_closest_res_to_spacing(
  dggs,
  spacing,
  round = "nearest",
  show_info = TRUE,
  metric = TRUE
)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- spacing:

  The desired spacing between the center of adjacent cells

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
res  <- dg_closest_res_to_spacing(dggs,1)
#> Resolution: 16, Area (km^2): 1.18491167242236, Spacing (km): 1.07508800966481, CLS (km): 1.22828188927244
dggs <- dgsetres(dggs,res)
```
