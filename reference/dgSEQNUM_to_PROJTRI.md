# Convert from SEQNUM to PROJTRI

Uses a discrete global grid system to convert between SEQNUM and PROJTRI
(see vignette for details)

## Usage

``` r
dgSEQNUM_to_PROJTRI(dggs, in_seqnum)
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

dgSEQNUM_to_PROJTRI(dggs, in_seqnum)
} # }
```
