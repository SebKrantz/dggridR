# Get largest cell id for a dggs

Cells are labeled 1-N. This function returns N. This is useful if you
want to choose cells from the dggs randomly.

## Usage

``` r
dgmaxcell(dggs, res = NA)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- res:

  If NA, use the resolution specified by the dggs. Otherwise, override
  the resolution.

## Value

The maximum cell id.

## Examples

``` r
#Choose a set of cells randomly distributed over the Earth
library(dggridR)
dggs    <- dgconstruct(spacing=1000, metric=FALSE, resround='down')
#> Resolution: 3, Area (mi^2): 1173851.79791229, Spacing (mi): 843.496246531419, CLS (mi): 964.285490648183
N       <- 100                                 #Number of cells
maxcell <- dgmaxcell(dggs)                     #Get maximum cell id
cells   <- sample(1:maxcell, N, replace=FALSE) #Choose random cells
grid    <- dgcellstogrid(dggs,cells) #Get grid
```
