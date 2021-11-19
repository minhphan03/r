## set.seed() & .Random.seed

Syntax:

`set.seed(seed)`

The purpose of the R `set.seed` function is to allow you to set a seed in R. Setting a seed in R means to initialize a pseudorandom number generator. 

##### Why set seed?

When using functions that sample pseudorandom numbers, each time you  execute them you will obtain a different result. Consider, for instance, that you want to sample 5 numbers from a Normal distribution. For that  purpose you could type `rnorm(5)` and it would return 5 outputs (values) but if you run that again, it would give out 5 different values. This implies that the code is not reproducible, because you don’t know the seed that R used to generate that sequence.

This is useful for creating simulations or random objects that can be **reproduced**.

##### Saving the seed by using `.Random.seed`

```r
set.seed(1)
x <- .Random.seed
rnorm(5)

y <- .Random.seed
rnorm(5)

# .Random.seed is not equal in both cases
identical(x, y) # FALSE

```

Because seed is regenerated every time you run a distribution, you have to save the seed if you want to achieve the run again. 

Big thanks to [R Coder](https://r-coder.com/set-seed-r/) for the resources.

