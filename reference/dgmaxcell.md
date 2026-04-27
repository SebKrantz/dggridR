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
head(grid)
#> Simple feature collection with 6 features and 1 field
#> Geometry type: POLYGON
#> Dimension:     XY
#> Bounding box:  xmin: -152.1121 ymin: -46.44662 xmax: 138.45 ymax: 44.09063
#> Geodetic CRS:  WGS 84
#>   seqnum                       geometry
#> 1    153 POLYGON ((-107.2003 -19.871...
#> 2     74 POLYGON ((1.444112 -33.8171...
#> 3    228 POLYGON ((122.6695 -15.5462...
#> 4    146 POLYGON ((-135.3153 -18.547...
#> 5    122 POLYGON ((129.5337 44.09063...
#> 6     49 POLYGON ((-30.28484 15.9045...
```
