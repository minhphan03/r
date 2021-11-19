### generate()

Syntax:

```r
generate(x, reps = 1, type = NULL, variables = !!response_expr(x), ...)
```

Arguments:

* `x`: A data frame that can be coerced into a tibble.
* `type`: The method used to generate resamples of the observed data reflecting the null hypothesis. Currently one of "bootstrap", "permute", or "draw"

Provide the number of resamples from the population and the type of resampling to do, which is "bootstrap" in the case of constructing a confidence interval.

Example:

```R
samp %>% specify(response = EnvPolicy, success = "Yes") %>% generate(reps = 1000, type = "bootstrap")
```

