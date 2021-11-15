### geom_bar() / geom_col()

There are two types of bar charts: `geom_bar()` and `geom_col()`. `geom_bar()` makes the height of the bar proportional to the number of cases in each group (or if the `weight` aesthetic is supplied, the sum of the weights). If you want the heights of the bars to represent values in the data, use `geom_col()` instead.

`geom_bar()`/`geom_col()`: create bar charts, in which we have the arguments:

-  `position= `: the style declared in this part affects the fill argument in the `aes()` function
   * either "fill" stack bars and standardizes each stack to have constant height
   * or "dodge" to place the bars side by side. 
-  in effect, `geom_bar()` uses `stat_count()` by default: it counts the number of cases at each x position. `geom_col(…)` is `geom_bar(stat = “identity”)`
-  If it is `stat = "identity"` , we are asking R to use the y-value we provide for the dependent variable. 
-  that is, if you already have a data frame with neat, already manipulated (like a two way contingency table), you can skip adding columns into the arguments into the `ggplot()` function for summarizing and go straight to `geom_col()` and use the `aes()` function inside it to declare the columns that you want to put into.
-  **YOU CAN ADD `aes()` FUNCTION TO ANY OF THE GEOM FUNCTIONS**

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

