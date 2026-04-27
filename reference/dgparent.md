# Return parent cell ID for each input cell

For each cell ID in `cells` at the current grid resolution, returns the
ID of its parent cell at resolution `dggs\$res - 1`. Only hexagonal
grids are supported.

## Usage

``` r
dgparent(dggs, cells)
```

## Arguments

- dggs:

  A dggs object from
  [`dgconstruct()`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md).
  The parent cells will be at `dggs\$res - 1`.

- cells:

  Integer vector of cell sequence numbers (SEQNUM)

## Value

A data frame with columns `seqnum` (the input cell) and `parent` (the
parent cell ID at resolution - 1).

## Examples

``` r
library(dggridR)
dgparent(dgconstruct(res=4), c(1, 2))
#>   seqnum parent
#> 1      1      1
#> 2      2      2
```
