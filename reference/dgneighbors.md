# Return neighboring cell IDs for each input cell

For each cell ID in `cells`, returns the IDs of all adjacent cells.
Triangle grids are not supported.

## Usage

``` r
dgneighbors(dggs, cells)
```

## Arguments

- dggs:

  A dggs object from
  [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md)

- cells:

  Integer vector of cell sequence numbers (SEQNUM)

## Value

A data frame with columns `seqnum` (the input cell) and `neighbor` (each
adjacent cell ID).

## Examples

``` r
library(dggridR)
dgneighbors(dgconstruct(res=3), c(1, 2, 3))
#>    seqnum neighbor
#> 1       1       34
#> 2       1       61
#> 3       1       88
#> 4       1      115
#> 5       1        7
#> 6       2        8
#> 7       2        5
#> 8       2      133
#> 9       2      136
#> 10      2      250
#> 11      3        9
#> 12      3        6
#> 13      3      124
#> 14      3      127
#> 15      3      133
#> 16      3        5
```
