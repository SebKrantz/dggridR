# Convert from Q2DI to GEO

Uses a discrete global grid system to convert between Q2DI and GEO (see
vignette for details)

## Usage

``` r
dgQ2DI_to_GEO(dggs, in_quad, in_i, in_j)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- in_quad:

  Vector of quad numbers

- in_i:

  Vector of quadrant i values

- in_j:

  Vector of quadrant j values

## Value

Returns a dggs object which can be passed to other dggridR functions

## Examples

``` r
if (FALSE) { # \dontrun{
library(dggridR)
dggs <- dgconstruct(res=20)

dgQ2DI_to_GEO(dggs, in_quad, in_i, in_j)
} # }
```
