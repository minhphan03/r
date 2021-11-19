## sample() & sample_n()

Used to generate uniform distribution integer values

`sample(x, size, replace = FALSE)`

* `x` is the vector that you want to pull samples from, or it can just be a series of numbers
* `replace` argument specifies if user wants to sample with or without replacement.

Ex:

```R
sample(1:12, 15, replace = TRUE)
[1]  4  4  3  4  4 11  5  7 12  6  7 11
[13]  4 11  8
```

`sample_n()`, on the other hand, does not require a vector but a table (tbl) to work on:

```R
sample_n(tbl, size, replace = FALSE, weight = NULL, .env = NULL, ...)
```

* sampling weight: In mathematical notation, if a unit is included in the sample with probability $P_i$, then its  base weight, denoted by $w_i$ , is given by $w_i=1/P_i$. This must evaluate to a vector of non-negative numbers the same length as the input. Weights are automatically standardized to sum to 1.
* Use sampling weight to note that there is unequal probability of getting sampled and so the chance of getting sampled is different among objects.

Example:

```R
sample_n(mtcars, 10, weight = mpg)
#>                    mpg cyl  disp  hp drat    wt  qsec vs am gear carb
#> Merc 450SLC       15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
#> Volvo 142E        21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2
#> Merc 280C         17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
#> Toyota Corolla    33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
#> Chrysler Imperial 14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
#> Datsun 710        22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
#> Merc 230          22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
#> Fiat X1-9         27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
#> Merc 450SE        16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
#> Hornet 4 Drive    21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1

```

