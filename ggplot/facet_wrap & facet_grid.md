## facet_wrap() & facet_grid()

1. [facet_wrap()](#facet_wrap())

2. [facet_grid()](#facet_grid())

### facet_wrap()

Syntax:

```R
facet_wrap(
  facets,
  nrow = NULL,
  ncol = NULL,
  scales = "fixed",
  shrink = TRUE,
  labeller = "label_value",
  as.table = TRUE,
  switch = NULL,
  drop = TRUE,
  dir = "h",
  strip.position = "top"
)
```

Arguments:

* `facets`: A set of variables or expressions quoted by `vars()` and defining faceting groups on the rows or columns dimension. The variables can be named (the names are passed to `labeller`). **The variable can be a column, formatted ~{column name} **

With a single function you can split a single plot into many related plots using `facet_wrap()` or `facet_grid()`.

Example:

##### Before `facet_wrap()`

```r
ggplot(data = marvel_count, aes(year, n)) +
  geom_line(color = "steelblue",size = 1) +
  geom_point(color="steelblue") + 
  labs(title = "New Marvel characters by year",
       subtitle = "(limited to characters with more than 100 appearances)",
       y = "Count of new characters", x = "")
```

Result:

![](http://zevross.com/blog/wp-content/uploads/2019/03/facet_plot1.png)

##### After facet_wrap()

```r
ggplot(data = marvel_count, aes(year, n)) +
  geom_line(color = "steelblue", size = 1) +
  geom_point(color="steelblue") + 
  labs(title = "New Marvel characters by alignment",
       subtitle = "(limited to characters with more than 100 appearances)",
       y = "Count of new characters", x = "") + 
  facet_wrap(~ align)
```

Result:

![](http://www.zevross.com/blog/wp-content/uploads/2019/03/facet_plot2_wrap.png)



### facet_grid()

Rather than allowing `facet_wrap()` to decide the layout of rows and columns you can use `facet_grid()` for organization and customization.

The syntax follows the pattern `facet_grid(row_variable ~ column_variable)` and we can apply that syntax to our plot from before with `align` as the row variable and `gender` as the column variable.

Example:

```r
ggplot(data = marvel_count, aes(year, n)) +
  geom_line(color = "steelblue", size = 1) +
  geom_point(color = "steelblue") + 
  labs(title = "New Marvel characters by alignment & gender",
       subtitle = "(limited to characters with more than 100 appearances)",
       y = "Count of new characters", x = "") + 
  facet_grid(align ~ gender) 
```

Result:

![](http://zevross.com/blog/wp-content/uploads/2019/03/facet_plot_5_grid.png)

(Thank you Joshua Ebner for the examples in this tutorial. The full post can be found [here](https://www.sharpsightlabs.com/blog/mutate-in-r/))

