## ggplot()

`ggplot()` initializes a ggplot object. It can be used to declare the input data frame for a graphic and to specify the set of plot aesthetics intended to be common throughout all subsequent layers unless specifically overridden.

```
ggplot(data = NULL, mapping = aes(), ..., environment = parent.frame())
```

* `ggplot()`: create a new ggplot object

Other 

* `labs()`: modify axis, legend, and plot labels
  * `y=`: change legend name of the vertical axis
  * `title=`: change title
  * `subtitle=`: change the subtitle (the *additional data* below the title)
* `xlab(axis_name)`: change the title of the x axis
* `facet_wrap(~{column name})`: separate the original plot into a multi-panel bar plot in regard to the column name
* `coord_flip()` : flip the coordinates

