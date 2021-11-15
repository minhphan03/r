### geom_dotplot()

In a dot plot, the width of a dot corresponds to the bin width (or maximum width, depending on the binning algorithm), and dots are stacked, with each dot representing one observation.

List of arguments:

```
geom_dotplot(
  mapping = NULL,
  data = NULL,
  position = "identity",
  ...,
  binwidth = NULL,
  binaxis = "x",
  method = "dotdensity",
  binpositions = "bygroup",
  stackdir = "up",
  stackratio = 1,
  dotsize = 1,
  stackgroups = FALSE,
  origin = NULL,
  right = TRUE,
  width = 0.9,
  drop = FALSE,
  na.rm = FALSE,
  show.legend = NA,
  inherit.aes = TRUE
)
```

* `dot_size=`: adjust the size of the dots in the dotplot -- aesthetics thingy
* `methods=`: either "dotdensity" (default) for dot-density binning, or "histodot" for fixed bin widths (like stat_bin)
* `fill=` color of the filled dots
* `stroke=` a numerical value for the stroke size of the dots

Example:

```R
origdiff <- PermsOut$diff_orig[1]
p1 <- ggplot(data = PermsOut, aes(x = diff_perm)) +
         geom_dotplot(dotsize = 0.25, method="histodot", binwidth=.01) + xlab("Old - New") + geom_vline(xintercept = origdiff, col="Red")

```

