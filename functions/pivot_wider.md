## pivot_wider()

used to "widen" the data, increasing the number of columns and decreasing teh number of rows.

Arguments:

* data: the dataframe/table to pivot
* names_from : describe which column(s) to get the name of the output column from
* values_from: describe which columns to get the cell values from
* values_fill: fill in the missing (N/A) values with a default value set

Example: from tidyr package 

```r
fish_encounters
#> # A tibble: 114 × 3
#>    fish  station  seen
#>    <fct> <fct>   <int>
#>  1 4842  Release     1
#>  2 4842  I80_1       1
#>  3 4842  Lisbon      1
#>  4 4842  Rstr        1
#>  5 4842  Base_TD     1
#>  6 4842  BCE         1
#>  7 4842  BCW         1
#>  8 4842  BCE2        1
#>  9 4842  BCW2        1
#> 10 4842  MAE         1
#> # … with 104 more rows
```

Applying the pivot_wider to use the values in the station columns to be the columns, and use the values in the seen column to indicate whether it is "seen" or not:

```r
fish_encounters %>%
  pivot_wider(names_from = station, values_from = seen, values_fill = 0)
#> # A tibble: 19 × 12
#>    fish  Release I80_1 Lisbon  Rstr Base_TD   BCE   BCW  BCE2  BCW2   MAE   MAW
#>    <fct>   <int> <int>  <int> <int>   <int> <int> <int> <int> <int> <int> <int>
#>  1 4842        1     1      1     1       1     1     1     1     1     1     1
#>  2 4843        1     1      1     1       1     1     1     1     1     1     1
#>  3 4844        1     1      1     1       1     1     1     1     1     1     1
#>  4 4845        1     1      1     1       1     0     0     0     0     0     0
#>  5 4847        1     1      1     0       0     0     0     0     0     0     0
#>  6 4848        1     1      1     1       0     0     0     0     0     0     0
#>  7 4849        1     1      0     0       0     0     0     0     0     0     0
#>  8 4850        1     1      0     1       1     1     1     0     0     0     0
#>  9 4851        1     1      0     0       0     0     0     0     0     0     0
#> 10 4854        1     1      0     0       0     0     0     0     0     0     0
#> 11 4855        1     1      1     1       1     0     0     0     0     0     0
#> 12 4857        1     1      1     1       1     1     1     1     1     0     0
#> 13 4858        1     1      1     1       1     1     1     1     1     1     1
#> 14 4859        1     1      1     1       1     0     0     0     0     0     0
#> 15 4861        1     1      1     1       1     1     1     1     1     1     1
#> 16 4862        1     1      1     1       1     1     1     1     1     0     0
#> 17 4863        1     1      0     0       0     0     0     0     0     0     0
#> 18 4864        1     1      0     0       0     0     0     0     0     0     0
#> 19 4865        1     1      1     0       0     0     0     0     0     0     0

```

We can also combine the names_from and values_from to create matrices of values. In the example below, from two main columns (income and rent), by combining with the values in the estimate and moe columns, we can create a full functional table for viewing and comparing.

```r
# Generate column names from multiple variables
us_rent_income
#> # A tibble: 104 × 5
#>    GEOID NAME       variable estimate   moe
#>    <chr> <chr>      <chr>       <dbl> <dbl>
#>  1 01    Alabama    income      24476   136
#>  2 01    Alabama    rent          747     3
#>  3 02    Alaska     income      32940   508
#>  4 02    Alaska     rent         1200    13
#>  5 04    Arizona    income      27517   148
#>  6 04    Arizona    rent          972     4
#>  7 05    Arkansas   income      23789   165
#>  8 05    Arkansas   rent          709     5
#>  9 06    California income      29454   109
#> 10 06    California rent         1358     3
#> # … with 94 more rows
us_rent_income %>%
  pivot_wider(names_from = variable, values_from = c(estimate, moe))
#> # A tibble: 52 × 6
#>    GEOID NAME                 estimate_income estimate_rent moe_income moe_rent
#>    <chr> <chr>                          <dbl>         <dbl>      <dbl>    <dbl>
#>  1 01    Alabama                        24476           747        136        3
#>  2 02    Alaska                         32940          1200        508       13
#>  3 04    Arizona                        27517           972        148        4
#>  4 05    Arkansas                       23789           709        165        5
#>  5 06    California                     29454          1358        109        3
#>  6 08    Colorado                       32401          1125        109        5
#>  7 09    Connecticut                    35326          1123        195        5
#>  8 10    Delaware                       31560          1076        247       10
#>  9 11    District of Columbia           43198          1424        681       17
#> 10 12    Florida                        25952          1077         70        3
#> # … with 42 more rows

```

