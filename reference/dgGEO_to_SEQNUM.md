# Convert from GEO to SEQNUM

Uses a discrete global grid system to convert between GEO and SEQNUM
(see vignette for details)

## Usage

``` r
dgGEO_to_SEQNUM(dggs, in_lon_deg, in_lat_deg)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- in_lon_deg:

  Vector of longitude, in degrees

- in_lat_deg:

  Vector of latitude, in degrees

## Value

Returns a dggs object which can be passed to other dggridR functions

## Examples

``` r
if (FALSE) { # \dontrun{
library(dggridR)
dggs <- dgconstruct(res=20)

dgGEO_to_SEQNUM(dggs, in_lon_deg, in_lat_deg)
} # }
```
