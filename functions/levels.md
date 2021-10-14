## levels()

`levels()` provides access to the levels attribute of a variable.  The first form, `levels(x)` returns the value of the levels of its argument `x` and the second `levels(x) <- value` sets the attribute.

When you first get a data set, you will often notice that it contains factors with specific factor levels. However, sometimes you will want to change the names of these levels for clarity or other reasons. R allows you to do this with the function [`levels()`](http://www.rdocumentation.org/packages/base/functions/levels):

For example

```R
## assign individual levels
x <- gl(2, 4, 8)
levels(x)[1] <- "low"
levels(x)[2] <- "high"
x
```

```R
## combine some levels
z <- gl(3, 2, 12, labels = c("apple", "salad", "orange"))
z
levels(z) <- c("fruit", "veg", "fruit")
z
```

```R
levels(x) <- c(levels(x), "widowed")    # add new level "widowed"
x[3] <- "widowed"
```

