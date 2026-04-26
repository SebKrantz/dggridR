# Convert from SEQNUM to PLANE

Uses a discrete global grid system to convert between SEQNUM and PLANE
(see vignette for details)

## Usage

``` r
dgSEQNUM_to_PLANE(dggs, in_seqnum)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- in_seqnum:

  Globally unique number identifying the surface polygon

## Value

Returns a dggs object which can be passed to other dggridR functions

## Examples

``` r
if (FALSE) { # \dontrun{
library(dggridR)
dggs <- dgconstruct(res=20)

dgSEQNUM_to_PLANE(dggs, in_seqnum)
} # }
```
