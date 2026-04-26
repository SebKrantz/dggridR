# Aggregate point data into grid cells

Bins a set of lon/lat points — optionally with associated numeric values
— into the cells of a discrete global grid. Returns a data frame (no
geometry) with per-cell statistics (equivalent to DGGRID's
`BIN_POINT_VALS` / `BIN_POINT_PRESENCE` operations).

## Usage

``` r
dgbin_points(
  dggs,
  lon,
  lat,
  values = NULL,
  output_count = is.null(values),
  output_mean = !is.null(values),
  output_total = FALSE
)
```

## Arguments

- dggs:

  A dggs object from
  [`dgconstruct`](https://sebkrantz.github.io/dggridR/reference/dgconstruct.md).

- lon:

  Numeric vector of longitudes (decimal degrees).

- lat:

  Numeric vector of latitudes (decimal degrees).

- values:

  Optional numeric vector of values to aggregate (same length as
  `lon`/`lat`). If `NULL`, only point counts are computed.

- output_count:

  Logical. Return count of points per cell. Default: `TRUE` when
  `values` is `NULL`, `FALSE` otherwise.

- output_mean:

  Logical. Return mean of values per cell. Only meaningful when `values`
  is supplied. Default: `TRUE` when `values` is not `NULL`.

- output_total:

  Logical. Return total (sum) of values per cell. Only meaningful when
  `values` is supplied. Default: `FALSE`.

## Value

A data frame with a `seqnum` column (cell ID) plus whichever of `count`,
`mean`, `total` were requested.

## Examples

``` r
library(dggridR)
data(dgquakes)
dggs <- dgconstruct(spacing=1000, metric=FALSE, resround='down')
#> Resolution: 3, Area (mi^2): 1173851.79791229, Spacing (mi): 843.496246531419, CLS (mi): 964.285490648183

# Count earthquakes per cell
dgbin_points(dggs, dgquakes$lon, dgquakes$lat)
#> Warning: corrupt data frame: columns will be truncated or padded with NAs
#>     seqnum count
#> 1        1     0
#> 2        2  <NA>
#> 3        4  <NA>
#> 4        5  <NA>
#> 5        7  <NA>
#> 6        8  <NA>
#> 7       12  <NA>
#> 8       13  <NA>
#> 9       14  <NA>
#> 10      16  <NA>
#> 11      18  <NA>
#> 12      21  <NA>
#> 13      22  <NA>
#> 14      24  <NA>
#> 15      25  <NA>
#> 16      27  <NA>
#> 17      28  <NA>
#> 18      30  <NA>
#> 19      31  <NA>
#> 20      33  <NA>
#> 21      34  <NA>
#> 22      35  <NA>
#> 23      37  <NA>
#> 24      38  <NA>
#> 25      39  <NA>
#> 26      40  <NA>
#> 27      41  <NA>
#> 28      42  <NA>
#> 29      43  <NA>
#> 30      44  <NA>
#> 31      45  <NA>
#> 32      47  <NA>
#> 33      49  <NA>
#> 34      50  <NA>
#> 35      53  <NA>
#> 36      55  <NA>
#> 37      56  <NA>
#> 38      57  <NA>
#> 39      58  <NA>
#> 40      61  <NA>
#> 41      62  <NA>
#> 42      64  <NA>
#> 43      65  <NA>
#> 44      70  <NA>
#> 45      71  <NA>
#> 46      76  <NA>
#> 47      78  <NA>
#> 48      79  <NA>
#> 49      80  <NA>
#> 50      81  <NA>
#> 51      82  <NA>
#> 52      84  <NA>
#> 53      85  <NA>
#> 54      86  <NA>
#> 55      87  <NA>
#> 56      88  <NA>
#> 57      90  <NA>
#> 58      91  <NA>
#> 59      92  <NA>
#> 60      93  <NA>
#> 61      94  <NA>
#> 62      95  <NA>
#> 63      96  <NA>
#> 64      97  <NA>
#> 65      98  <NA>
#> 66      99  <NA>
#> 67     100  <NA>
#> 68     101  <NA>
#> 69     102  <NA>
#> 70     103  <NA>
#> 71     105  <NA>
#> 72     106  <NA>
#> 73     107  <NA>
#> 74     108  <NA>
#> 75     109  <NA>
#> 76     110  <NA>
#> 77     111  <NA>
#> 78     112  <NA>
#> 79     113  <NA>
#> 80     115  <NA>
#> 81     116  <NA>
#> 82     117  <NA>
#> 83     119  <NA>
#> 84     120  <NA>
#> 85     121  <NA>
#> 86     122  <NA>
#> 87     123  <NA>
#> 88     124  <NA>
#> 89     125  <NA>
#> 90     126  <NA>
#> 91     127  <NA>
#> 92     128  <NA>
#> 93     129  <NA>
#> 94     130  <NA>
#> 95     131  <NA>
#> 96     132  <NA>
#> 97     133  <NA>
#> 98     134  <NA>
#> 99     136  <NA>
#> 100    138  <NA>
#> 101    139  <NA>
#> 102    141  <NA>
#> 103    142  <NA>
#> 104    145  <NA>
#> 105    148  <NA>
#> 106    150  <NA>
#> 107    151  <NA>
#> 108    153  <NA>
#> 109    159  <NA>
#> 110    161  <NA>
#> 111    162  <NA>
#> 112    163  <NA>
#> 113    164  <NA>
#> 114    165  <NA>
#> 115    167  <NA>
#> 116    170  <NA>
#> 117    173  <NA>
#> 118    176  <NA>
#> 119    178  <NA>
#> 120    179  <NA>
#> 121    180  <NA>
#> 122    181  <NA>
#> 123    182  <NA>
#> 124    184  <NA>
#> 125    185  <NA>
#> 126    187  <NA>
#> 127    188  <NA>
#> 128    191  <NA>
#> 129    193  <NA>
#> 130    194  <NA>
#> 131    196  <NA>
#> 132    198  <NA>
#> 133    202  <NA>
#> 134    204  <NA>
#> 135    205  <NA>
#> 136    208  <NA>
#> 137    211  <NA>
#> 138    214  <NA>
#> 139    215  <NA>
#> 140    217  <NA>
#> 141    219  <NA>
#> 142    220  <NA>
#> 143    222  <NA>
#> 144    223  <NA>
#> 145    225  <NA>
#> 146    226  <NA>
#> 147    227  <NA>
#> 148    228  <NA>
#> 149    229  <NA>
#> 150    231  <NA>
#> 151    232  <NA>
#> 152    233  <NA>
#> 153    234  <NA>
#> 154    235  <NA>
#> 155    236  <NA>
#> 156    237  <NA>
#> 157    238  <NA>
#> 158    239  <NA>
#> 159    240  <NA>
#> 160    241  <NA>
#> 161    242  <NA>
#> 162    244  <NA>
#> 163    245  <NA>
#> 164    250  <NA>
#> 165    251  <NA>
#> 166    254  <NA>
#> 167    257  <NA>
#> 168    259  <NA>
#> 169    260  <NA>
#> 170    262  <NA>
#> 171    263  <NA>
#> 172    264  <NA>
#> 173    266  <NA>
#> 174    272  <NA>

# Aggregate magnitude per cell
dgbin_points(dggs, dgquakes$lon, dgquakes$lat, values=dgquakes$mag,
             output_count=TRUE, output_total=TRUE)
#> Warning: corrupt data frame: columns will be truncated or padded with NAs
#>     seqnum count     mean   total
#> 1        1 19914 4.222672 84090.3
#> 2        2  <NA>     <NA>    <NA>
#> 3        4  <NA>     <NA>    <NA>
#> 4        5  <NA>     <NA>    <NA>
#> 5        7  <NA>     <NA>    <NA>
#> 6        8  <NA>     <NA>    <NA>
#> 7       12  <NA>     <NA>    <NA>
#> 8       13  <NA>     <NA>    <NA>
#> 9       14  <NA>     <NA>    <NA>
#> 10      16  <NA>     <NA>    <NA>
#> 11      18  <NA>     <NA>    <NA>
#> 12      21  <NA>     <NA>    <NA>
#> 13      22  <NA>     <NA>    <NA>
#> 14      24  <NA>     <NA>    <NA>
#> 15      25  <NA>     <NA>    <NA>
#> 16      27  <NA>     <NA>    <NA>
#> 17      28  <NA>     <NA>    <NA>
#> 18      30  <NA>     <NA>    <NA>
#> 19      31  <NA>     <NA>    <NA>
#> 20      33  <NA>     <NA>    <NA>
#> 21      34  <NA>     <NA>    <NA>
#> 22      35  <NA>     <NA>    <NA>
#> 23      37  <NA>     <NA>    <NA>
#> 24      38  <NA>     <NA>    <NA>
#> 25      39  <NA>     <NA>    <NA>
#> 26      40  <NA>     <NA>    <NA>
#> 27      41  <NA>     <NA>    <NA>
#> 28      42  <NA>     <NA>    <NA>
#> 29      43  <NA>     <NA>    <NA>
#> 30      44  <NA>     <NA>    <NA>
#> 31      45  <NA>     <NA>    <NA>
#> 32      47  <NA>     <NA>    <NA>
#> 33      49  <NA>     <NA>    <NA>
#> 34      50  <NA>     <NA>    <NA>
#> 35      53  <NA>     <NA>    <NA>
#> 36      55  <NA>     <NA>    <NA>
#> 37      56  <NA>     <NA>    <NA>
#> 38      57  <NA>     <NA>    <NA>
#> 39      58  <NA>     <NA>    <NA>
#> 40      61  <NA>     <NA>    <NA>
#> 41      62  <NA>     <NA>    <NA>
#> 42      64  <NA>     <NA>    <NA>
#> 43      65  <NA>     <NA>    <NA>
#> 44      70  <NA>     <NA>    <NA>
#> 45      71  <NA>     <NA>    <NA>
#> 46      76  <NA>     <NA>    <NA>
#> 47      78  <NA>     <NA>    <NA>
#> 48      79  <NA>     <NA>    <NA>
#> 49      80  <NA>     <NA>    <NA>
#> 50      81  <NA>     <NA>    <NA>
#> 51      82  <NA>     <NA>    <NA>
#> 52      84  <NA>     <NA>    <NA>
#> 53      85  <NA>     <NA>    <NA>
#> 54      86  <NA>     <NA>    <NA>
#> 55      87  <NA>     <NA>    <NA>
#> 56      88  <NA>     <NA>    <NA>
#> 57      90  <NA>     <NA>    <NA>
#> 58      91  <NA>     <NA>    <NA>
#> 59      92  <NA>     <NA>    <NA>
#> 60      93  <NA>     <NA>    <NA>
#> 61      94  <NA>     <NA>    <NA>
#> 62      95  <NA>     <NA>    <NA>
#> 63      96  <NA>     <NA>    <NA>
#> 64      97  <NA>     <NA>    <NA>
#> 65      98  <NA>     <NA>    <NA>
#> 66      99  <NA>     <NA>    <NA>
#> 67     100  <NA>     <NA>    <NA>
#> 68     101  <NA>     <NA>    <NA>
#> 69     102  <NA>     <NA>    <NA>
#> 70     103  <NA>     <NA>    <NA>
#> 71     105  <NA>     <NA>    <NA>
#> 72     106  <NA>     <NA>    <NA>
#> 73     107  <NA>     <NA>    <NA>
#> 74     108  <NA>     <NA>    <NA>
#> 75     109  <NA>     <NA>    <NA>
#> 76     110  <NA>     <NA>    <NA>
#> 77     111  <NA>     <NA>    <NA>
#> 78     112  <NA>     <NA>    <NA>
#> 79     113  <NA>     <NA>    <NA>
#> 80     115  <NA>     <NA>    <NA>
#> 81     116  <NA>     <NA>    <NA>
#> 82     117  <NA>     <NA>    <NA>
#> 83     119  <NA>     <NA>    <NA>
#> 84     120  <NA>     <NA>    <NA>
#> 85     121  <NA>     <NA>    <NA>
#> 86     122  <NA>     <NA>    <NA>
#> 87     123  <NA>     <NA>    <NA>
#> 88     124  <NA>     <NA>    <NA>
#> 89     125  <NA>     <NA>    <NA>
#> 90     126  <NA>     <NA>    <NA>
#> 91     127  <NA>     <NA>    <NA>
#> 92     128  <NA>     <NA>    <NA>
#> 93     129  <NA>     <NA>    <NA>
#> 94     130  <NA>     <NA>    <NA>
#> 95     131  <NA>     <NA>    <NA>
#> 96     132  <NA>     <NA>    <NA>
#> 97     133  <NA>     <NA>    <NA>
#> 98     134  <NA>     <NA>    <NA>
#> 99     136  <NA>     <NA>    <NA>
#> 100    138  <NA>     <NA>    <NA>
#> 101    139  <NA>     <NA>    <NA>
#> 102    141  <NA>     <NA>    <NA>
#> 103    142  <NA>     <NA>    <NA>
#> 104    145  <NA>     <NA>    <NA>
#> 105    148  <NA>     <NA>    <NA>
#> 106    150  <NA>     <NA>    <NA>
#> 107    151  <NA>     <NA>    <NA>
#> 108    153  <NA>     <NA>    <NA>
#> 109    159  <NA>     <NA>    <NA>
#> 110    161  <NA>     <NA>    <NA>
#> 111    162  <NA>     <NA>    <NA>
#> 112    163  <NA>     <NA>    <NA>
#> 113    164  <NA>     <NA>    <NA>
#> 114    165  <NA>     <NA>    <NA>
#> 115    167  <NA>     <NA>    <NA>
#> 116    170  <NA>     <NA>    <NA>
#> 117    173  <NA>     <NA>    <NA>
#> 118    176  <NA>     <NA>    <NA>
#> 119    178  <NA>     <NA>    <NA>
#> 120    179  <NA>     <NA>    <NA>
#> 121    180  <NA>     <NA>    <NA>
#> 122    181  <NA>     <NA>    <NA>
#> 123    182  <NA>     <NA>    <NA>
#> 124    184  <NA>     <NA>    <NA>
#> 125    185  <NA>     <NA>    <NA>
#> 126    187  <NA>     <NA>    <NA>
#> 127    188  <NA>     <NA>    <NA>
#> 128    191  <NA>     <NA>    <NA>
#> 129    193  <NA>     <NA>    <NA>
#> 130    194  <NA>     <NA>    <NA>
#> 131    196  <NA>     <NA>    <NA>
#> 132    198  <NA>     <NA>    <NA>
#> 133    202  <NA>     <NA>    <NA>
#> 134    204  <NA>     <NA>    <NA>
#> 135    205  <NA>     <NA>    <NA>
#> 136    208  <NA>     <NA>    <NA>
#> 137    211  <NA>     <NA>    <NA>
#> 138    214  <NA>     <NA>    <NA>
#> 139    215  <NA>     <NA>    <NA>
#> 140    217  <NA>     <NA>    <NA>
#> 141    219  <NA>     <NA>    <NA>
#> 142    220  <NA>     <NA>    <NA>
#> 143    222  <NA>     <NA>    <NA>
#> 144    223  <NA>     <NA>    <NA>
#> 145    225  <NA>     <NA>    <NA>
#> 146    226  <NA>     <NA>    <NA>
#> 147    227  <NA>     <NA>    <NA>
#> 148    228  <NA>     <NA>    <NA>
#> 149    229  <NA>     <NA>    <NA>
#> 150    231  <NA>     <NA>    <NA>
#> 151    232  <NA>     <NA>    <NA>
#> 152    233  <NA>     <NA>    <NA>
#> 153    234  <NA>     <NA>    <NA>
#> 154    235  <NA>     <NA>    <NA>
#> 155    236  <NA>     <NA>    <NA>
#> 156    237  <NA>     <NA>    <NA>
#> 157    238  <NA>     <NA>    <NA>
#> 158    239  <NA>     <NA>    <NA>
#> 159    240  <NA>     <NA>    <NA>
#> 160    241  <NA>     <NA>    <NA>
#> 161    242  <NA>     <NA>    <NA>
#> 162    244  <NA>     <NA>    <NA>
#> 163    245  <NA>     <NA>    <NA>
#> 164    250  <NA>     <NA>    <NA>
#> 165    251  <NA>     <NA>    <NA>
#> 166    254  <NA>     <NA>    <NA>
#> 167    257  <NA>     <NA>    <NA>
#> 168    259  <NA>     <NA>    <NA>
#> 169    260  <NA>     <NA>    <NA>
#> 170    262  <NA>     <NA>    <NA>
#> 171    263  <NA>     <NA>    <NA>
#> 172    264  <NA>     <NA>    <NA>
#> 173    266  <NA>     <NA>    <NA>
#> 174    272  <NA>     <NA>    <NA>
```
