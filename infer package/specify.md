## specify()

`specify()` is used to specify which columns in the supplied data frame are the relevant response (and, if applicable, explanatory) variables. Note that character variables are converted to `factor`s.

Syntax:

```R
specify(x, formula, response = NULL, explanatory = NULL, success = NULL)
```

Arguments:

* `x`: a data frame / table that can be coerced into a tibble
* response: The variable name in `x` that will serve as the response. This is an alternative to using the `formula` argument. 

Example:

```r
samp %>% specify(response = EnvPolicy, success = "Yes")
```

