## factor()

Factors are used to represent categorical data. Factors can be ordered or unordered and are an important class for statistical analysis and for plotting.

Once created, factors can only contain a pre-defined set values, known as *levels*.

```R
sex <- factor(c("male", "female", "female", "male"))
```

R will assign `1` to the level `"female"` and `2` to the level `"male"` (because `f` comes before `m`, even though the first element in this vector is `"male"`). You can check this by using the function `levels()`, and check the number of levels using `nlevels()`



Sometimes, the order of the factors does not matter, other times you might want to specify the order because it is meaningful (e.g., “low”, “medium”, “high”) or it is required by particular type of analysis. Additionally, specifying the order of the levels allows us to compare levels:

```R
food <- factor(c("low", "high", "medium", "high", "low", "medium", "high"))
levels(food)
```

In this case, you haven't specified the order of the levels, so if you use the `min` function to ask for the lowest level, it will result in an error. 

Therefore, you must add a parameter to declare that there is an ordered level in your factoring establishment:

```R
food <- factor(food, levels = c("low", "medium", "high"), ordered = TRUE)
levels(food)
```

```R
exercise <- factor(c("l", "n", "n", "i", "l"), levels = c("n", "l", "i"), ordered = TRUE)
```

