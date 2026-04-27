# Return the coordinates constituting the boundary of cells within a specified region

Note: This may generate odd results for very large rectangles, because
putting rectangles on spheres is weird... as you should know, if you're
using this package.

## Usage

``` r
dgrectgrid(
  dggs,
  minlat = -1,
  minlon = -1,
  maxlat = -1,
  maxlon = -1,
  cellsize = 0.1,
  ...
)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- minlat:

  Minimum latitude of region of interest

- minlon:

  Minimum longitude of region of interest

- maxlat:

  Maximum latitude of region of interest

- maxlon:

  Maximum longitude of region of interest

- cellsize:

  Distance, in degrees, between the sample points used to generate the
  grid. Small values yield long generation times while large values may
  omit cells.

- ...:

  Further arguments passed to
  [`dgcellstogrid`](https://sebkrantz.github.io/dggridR/reference/dgcellstogrid.md).

## Value

Returns an sf object. If `!is.na(savegrid)`, returns a filename.

## Examples

``` r
library(dggridR)
dggs <- dgconstruct(spacing=1000,metric=FALSE,resround='down')
#> Resolution: 3, Area (mi^2): 1173851.79791229, Spacing (mi): 843.496246531419, CLS (mi): 964.285490648183

#Get grid cells for the conterminous United States
grid <- dgrectgrid(dggs,
               minlat=24.7433195, minlon=-124.7844079,
               maxlat=49.3457868, maxlon=-66.9513812)
head(grid)
#> Simple feature collection with 6 features and 1 field
#> Geometry type: POLYGON
#> Dimension:     XY
#> Bounding box:  xmin: -137.6528 ymin: 14.37895 xmax: -64.03822 ymax: 37.12808
#> Geodetic CRS:  WGS 84
#>   seqnum                       geometry
#> 1     23 POLYGON ((-122.2927 27.605,...
#> 2     27 POLYGON ((-107.6792 27.8298...
#> 3    139 POLYGON ((-93.43959 26.6096...
#> 4    142 POLYGON ((-78.75 24.90997, ...
#> 5     35 POLYGON ((-64.06041 26.6096...
#> 6     29 POLYGON ((-73.7367 37.12808...
```
