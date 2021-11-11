## ggplot()

* `ggplot()`: create a new ggplot object
* `aes()`: construct aesthetic mappings
  * `x= {column name}`: specify the values/factors on the x axis
  * `fill= {column name}`: for stacks, we can provide `fill=` instead of `y=` for the vertical values (idk why)
* `geom_bar()`/`geom_col()`: create bar charts, in which we have the arguments:
  -  `position= `: the style declared in this part affects the fill argument in the `aes()` function
    * either "fill" stack bars and standardizes each stack to have constant height
    * or "dodge" to place the bars side by side. 
  - in effect, `geom_bar()` uses `stat_count()` by default: it counts the number of cases at each x position. `geom_col(…)` is `geom_bar(stat = “identity”)`
  - that is, if you already have a data frame with neat, already manipulated (like a two way contingency table), you can skip adding columns into the arguments into the `ggplot()` function for summarizing and go straight to `geom_col()` and use the `aes()` function inside it to declare the columns that you want to put into.
  - **YOU CAN ADD `aes()` FUNCTION TO ANY OF THE GEOM FUNCTIONS**

* `labs()`: modify axis, legend, and plot labels
  * `y=`: change legend name of the vertical axis

* `facet_wrap(~{column name})`: separate the original plot into a multi-panel bar plot in regard to the column name

For example:

```R
groupPI_partyID.df %>% ggplot() +
  geom_col(aes(x=Response,y=Prop,fill=PartyID), position="dodge" ) +
  facet_wrap(~PartyID)
```

```r
p2 = ggplot(gallup_ed, aes(x = Education, fill= Response)) + 
  geom_bar(position = "fill") +
  labs(y = "Proportion")
p2
```

