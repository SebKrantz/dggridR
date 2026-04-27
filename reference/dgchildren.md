# Return immediate child cell IDs for each input cell

For each cell ID in `cells` at the current grid resolution, returns the
IDs of its child cells at resolution `dggs\$res + 1`. Only hexagonal
grids are supported.

## Usage

``` r
dgchildren(dggs, cells)
```

## Arguments

- dggs:

  A dggs object from
  [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md).
  The child cells will be at `dggs\$res + 1`.

- cells:

  Integer vector of cell sequence numbers (SEQNUM)

## Value

A data frame with columns `seqnum` (the input cell) and `child` (each
child cell ID at resolution + 1).

## Examples

``` r
library(dggridR)
dgchildren(dgconstruct(res=3), c(1, 2))
#>    seqnum child
#> 1       1     1
#> 2       1    91
#> 3       1   172
#> 4       1   253
#> 5       1   334
#> 6       1    10
#> 7       2     2
#> 8       2    11
#> 9       2    12
#> 10      2     3
#> 11      2   406
#> 12      2   739
```
