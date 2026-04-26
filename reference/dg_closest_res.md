# Determine an appropriate grid resolution based on input data.

This is a generic function that is used to determine an appropriate
resolution given an area, cell spacing, or correlated length scale. It
does so by extracting the appropriate length/area column and searching
it for a value close to the input.

## Usage

``` r
dg_closest_res(
  dggs,
  col,
  val,
  round = "nearest",
  show_info = TRUE,
  metric = TRUE
)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- col:

  Column in which to search for a close value. Should be: area_km,
  spacing_km, or cls_km.

- val:

  The value to search for

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
res  <- dg_closest_res(dggs,'area_km',1)
#> Resolution: 16, Area (km^2): 1.18491167242236, Spacing (km): 1.07508800966481, CLS (km): 1.22828188927244
dggs <- dgsetres(dggs,res)
```
