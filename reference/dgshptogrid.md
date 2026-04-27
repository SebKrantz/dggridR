# Return boundary coordinates for cells intersecting a shapefile

Returns the coordinates constituting the boundary of a set of cells
which intersect or are contained by a polygon (or polygons) specified in
a shapefile. Note that grid cells are also generated for holes in the
shapefile's polygon(s).

Note that coordinates in the shapefile must be rounded to check polygon
intersections. Currently this round preserves eight decimal digits of
precision.

The eighth decimal place is worth up to 1.1 mm of precision: this is
good for charting the motions of tectonic plates and the movements of
volcanoes. Permanent, corrected, constantly-running GPS base stations
might be able to achieve this level of accuracy.

In other words: you should be just fine with this level of precision.

## Usage

``` r
dgshptogrid(dggs, shpfname, cellsize = 0.1, ...)
```

## Arguments

- dggs:

  A dggs object from dgconstruct()

- shpfname:

  Either a sf data frame or the file name of the shapefile. Filename
  should end with '.shp'.

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

dggs <- dgconstruct(spacing=25, metric=FALSE, resround='nearest')
#> Resolution: 9, Area (mi^2): 1610.22194501, Spacing (mi): 31.2406017233859, CLS (mi): 35.6922386250717
south_africa_grid <- dgshptogrid(dggs,dg_shpfname_south_africa())
#> Reading layer `ZAF_adm0' from data source 
#>   `/home/runner/work/_temp/Library/dggridR/extdata' using driver `ESRI Shapefile'
#> Simple feature collection with 1 feature and 1 field
#> Geometry type: MULTIPOLYGON
#> Dimension:     XY
#> Bounding box:  xmin: 16.45802 ymin: -46.93639 xmax: 37.87945 ymax: -22.14108
#> CRS:           NA
head(south_africa_grid)
#> Simple feature collection with 6 features and 1 field
#> Geometry type: POLYGON
#> Dimension:     XY
#> Bounding box:  xmin: 16.05806 ymin: -47.3298 xmax: 20.26694 ymax: -46.41935
#> Geodetic CRS:  WGS 84
#>   seqnum                       geometry
#> 1  57929 POLYGON ((16.69582 -46.4532...
#> 2  58092 POLYGON ((17.3761 -46.73251...
#> 3  58173 POLYGON ((18.00873 -46.5391...
#> 4  58336 POLYGON ((18.69427 -46.8076...
#> 5  58417 POLYGON ((19.3212 -46.60332...
#> 6  58580 POLYGON ((20.01159 -46.8617...
```
