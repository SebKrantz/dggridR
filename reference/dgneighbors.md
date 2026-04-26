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
dggs <- dgconstruct(res=3)
nbrs <- dgneighbors(dggs, c(1, 2, 3))
```
