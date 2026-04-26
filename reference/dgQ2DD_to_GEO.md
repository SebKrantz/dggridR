# Convert from Q2DD to GEO

Uses a discrete global grid system to convert between Q2DD and GEO (see
vignette for details)

## Usage

``` r
dgQ2DD_to_GEO(dggs, in_quad, in_qx, in_qy)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- in_quad:

  Vector of quad numbers

- in_qx:

  Vector of quadrant x values

- in_qy:

  Vector of quadrant y values

## Value

Returns a dggs object which can be passed to other dggridR functions

## Examples

``` r
if (FALSE) { # \dontrun{
library(dggridR)
dggs <- dgconstruct(res=20)

dgQ2DD_to_GEO(dggs, in_quad, in_qx, in_qy)
} # }
```
