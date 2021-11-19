## get_ci() / get_confidence_interval()

Syntax:

```R
get_confidence_interval(x, level = 0.95, type = NULL, point_estimate = NULL)

get_ci(x, level = 0.95, type = NULL, point_estimate = NULL)
```

Arguments:

* `x`: a distribution / a data frame / table that contained data that was transformed using `calculate()` or `fit()` functions. This object should have been passed to `generate()` function being supplied to the mentioned functions above. **IF passed using the pipe %>%, don't need to specify `x`**
* `level`: the confidence level.