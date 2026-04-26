# Verify that a dggs object has appropriate values

Verify that a dggs object has appropriate values

## Usage

``` r
dgverify(dggs)
```

## Arguments

- dggs:

  The dggs object to be verified

## Value

The function has no return value. A stop signal is raised if the object
is misspecified

## Examples

``` r
library(dggridR)
dggs <- dgconstruct(res=20)
dgverify(dggs)
```
