# Return boundary coordinates for specified cells

Returns the coordinates constituting the boundary of a specified set of
cells. Duplicates are eliminated to reduce processing and storage
requirements.

## Usage

``` r
dgcellstogrid(dggs, cells, savegrid = NA, return_sf = TRUE, densify = 0L)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- cells:

  The cells to get the boundaries of

- savegrid:

  If savegrid is set to a file path, then a shapefile containing the
  grid is written to that path and the filename is returned. No other
  manipulations are done. Default: NA (do not save grid, return it)

- return_sf:

  logical. If `FALSE`, a long-format data frame giving the coordinates
  of the vertices of each cell is returned. This is is considerably
  faster and more memory efficient than creating an sf data frame.

- densify:

  Integer. Number of extra vertices to add along each cell edge (0 =
  none). Larger values produce smoother boundaries for coarse-resolution
  cells. Default: 0.

## Value

Returns an sf object. If `!is.na(savegrid)`, returns a filename.

## Examples

``` r
library(dggridR)
data(dgquakes)

#Construct a grid with cells about ~1000 miles wide
dggs          <- dgconstruct(spacing=1000,metric=FALSE)
#> Resolution: 3, Area (mi^2): 1173851.79791229, Spacing (mi): 843.496246531419, CLS (mi): 964.285490648183
dgquakes$cell <- dgGEO_to_SEQNUM(dggs,dgquakes$lat,dgquakes$lon)$seqnum

#Get grid cells for the earthquakes identified
grid          <- dgcellstogrid(dggs, dgquakes$cell)
```
