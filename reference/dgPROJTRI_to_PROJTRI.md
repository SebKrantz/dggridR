# Convert from PROJTRI to PROJTRI

Uses a discrete global grid system to convert between PROJTRI and
PROJTRI (see vignette for details)

## Usage

``` r
dgPROJTRI_to_PROJTRI(dggs, in_tnum, in_tx, in_ty)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- in_tnum:

  Vector of triangle numbers

- in_tx:

  Vector of triangle x values

- in_ty:

  Vector of triangle y values

## Value

Returns a dggs object which can be passed to other dggridR functions

## Examples

``` r
if (FALSE) { # \dontrun{
library(dggridR)
dggs <- dgconstruct(res=20)

dgPROJTRI_to_PROJTRI(dggs, in_tnum, in_tx, in_ty)
} # }
```
