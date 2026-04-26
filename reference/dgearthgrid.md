# Return the coordinates constituting the boundary of cells for the entire Earth

Note: If you have a high-resolution grid this may take a very long time
to execute.

## Usage

``` r
dgearthgrid(dggs, savegrid = NA, return_sf = TRUE, densify = 0L)
```

## Arguments

- dggs:

  A dggs object from dgconstruct().

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
# \donttest{
library(dggridR)
dggs         <- dgconstruct(res=20)
res          <- dg_closest_res_to_spacing(dggs,spacing=1000,round='down',metric=FALSE)
#> Resolution: 3, Area (mi^2): 1173851.79791229, Spacing (mi): 843.496246531419, CLS (mi): 964.285490648183
dggs         <- dgsetres(dggs,res)
gridfilename <- dgearthgrid(dggs,savegrid=tempfile(fileext=".shp")) #Save directly to a file
# }
```
