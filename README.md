
<!-- README.md is generated from README.Rmd. Please edit that file -->

# k5 <img src='man/figures/logo.png' align="right" height="139" />

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/k5)](https://CRAN.R-project.org/package=k5)
![Downloads](https://cranlogs.r-pkg.org/badges/grand-total/k5)
[![Codecov test
coverage](https://codecov.io/gh/k5cents/k5/graph/badge.svg?token=VCjNuCUEkS)](https://app.codecov.io/gh/k5cents/k5?branch=master')
[![R build
status](https://github.com/k5cents/k5/workflows/R-CMD-check/badge.svg)](https://github.com/k5cents/gluedown/actions)
<!-- badges: end -->

The goal of ‘k5’ is to offer miscellaneous quality of life functions
used by [Kiernan Nicholls](https://github.com/k5cents) during
interactive programming. They make things easier for me but are *bad*
for scripts and packages.

## Installation

You can install the release version of this package from
[CRAN](https://CRAN.R-project.org/package=k5):

``` r
install.packages("k5")
```

The development version can be installed from
[GitHub](https://github.com/k5cents/k5):

``` r
# install.packages("remotes")
remotes::install_github("k5cents/k5")
```

## Example

``` r
library(k5)
packageVersion("k5")
#> [1] '0.2.1'
```

A list of frequently used packages can be loaded from a file.

``` r
load_my_packages()
#> ✔ load 19 packages from
#> '/home/kiernan/R/x86_64-pc-linux-gnu-library/4.1/k5/PACKAGES'
```

Some functions wrap common combos like `mean(x %in% y)` or
`sum(is.na(x))`.

``` r
x <- c("VT", "NH", "ZZ", "ME", NA)
prop_in(x, state.abb)
#> [1] 0.75
count_na(x)
#> [1] 1
```

Some functions wrap functions from other packages with different
defaults.

``` r
dplyr::count(mtcars, cyl)
#>   cyl  n
#> 1   4 11
#> 2   6  7
#> 3   8 14

# sort and add fraction
k5::count2(mtcars, cyl)
#> # A tibble: 3 × 3
#>     cyl     n     p
#>   <dbl> <int> <dbl>
#> 1     8    14 0.438
#> 2     4    11 0.344
#> 3     6     7 0.219
```

There are also some handy shortcuts for the `.Last.value` tool.

``` r
df <- tail(mtcars, 50)
write_last()
#> ℹ `.Last.value` has class 'data.frame'
#> ✓ Saved tab-separated file '/tmp/RtmpFTaCH6/file15127cc7851b.tsv' (1.25K)
vc <- sample(state.name, 1000, replace = TRUE)
write_last()
#> ℹ `.Last.value` has class 'character'
#> ✓ Saved line-separated file '/tmp/RtmpFTaCH6/file151235b67c89.txt' (9.19K)
```

<!-- refs: start -->
<!-- refs: end -->
