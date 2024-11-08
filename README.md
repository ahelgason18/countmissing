Count Missing Values For All Columns By Group
================

<!-- README.md is generated from README.Rmd. Please edit that file -->

# countmissing

The goal of countmissing is to, given a data frame `data` and a column
`group`, `count_all_missing_by_group()`, create a new data frame with
one row per level of `group`. The first column of the output data frame
contains the levels of `group`, and the rest of the columns contain the
number of missing values for all columns in `data` except `group`.

## Installation

You can install the development version of countmissing from
[GitHub](https://github.com/) with, insert the following code into your
R Console. Make sure to install the countmissing package prior to
running count_all_missing_by_group():

``` r

install_github("ahelgason18/countmissing", ref = "0.1.0")
```

## Usage Example

This example demonstrates how to use the count_all_missing_by_group
function from the countmissing package to which creates a new data frame
with one row per level of `species`. The first column of the output data
frame contains the levels of `species`, and the rest of the columns
contain the number of missing values for each level of `species` for all
columns in `penguins` except `species`:

``` r
#Load necessary packages for the examples
library(countmissing)
library(dplyr)
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union
library(palmerpenguins)
```

Example 1:

``` r
example1 <- count_all_missing_by_group(penguins, species)
print(example1)
#> # A tibble: 3 × 8
#>   species   island bill_length_mm bill_depth_mm flipper_length_mm body_mass_g
#>   <fct>      <int>          <int>         <int>             <int>       <int>
#> 1 Adelie         0              1             1                 1           1
#> 2 Chinstrap      0              0             0                 0           0
#> 3 Gentoo         0              1             1                 1           1
#> # ℹ 2 more variables: sex <int>, year <int>
```

Example 2:

``` r

example2 <- penguins |> count_all_missing_by_group(species) 
print(example2)
#> # A tibble: 3 × 8
#>   species   island bill_length_mm bill_depth_mm flipper_length_mm body_mass_g
#>   <fct>      <int>          <int>         <int>             <int>       <int>
#> 1 Adelie         0              1             1                 1           1
#> 2 Chinstrap      0              0             0                 0           0
#> 3 Gentoo         0              1             1                 1           1
#> # ℹ 2 more variables: sex <int>, year <int>
```

Example 3:

``` r

example3 <- count_all_missing_by_group(penguins, species, .groups = "keep")
print(example3)
#> # A tibble: 3 × 8
#> # Groups:   species [3]
#>   species   island bill_length_mm bill_depth_mm flipper_length_mm body_mass_g
#>   <fct>      <int>          <int>         <int>             <int>       <int>
#> 1 Adelie         0              1             1                 1           1
#> 2 Chinstrap      0              0             0                 0           0
#> 3 Gentoo         0              1             1                 1           1
#> # ℹ 2 more variables: sex <int>, year <int>
```

## License

This package is licensed under the MIT license.
