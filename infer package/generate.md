### generate()

*syntax goes here*

provide the number of resamples from the population and the type of resampling to do, which is "bootstrap" in the case of constructing a confidence interval.

Example:

```R
samp %>% specify(response = EnvPolicy, success = "Yes") %>% generate(reps = 1000, type = "bootstrap")
```

