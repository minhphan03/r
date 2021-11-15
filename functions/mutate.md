## mutate() & transmute()

`mutate()` adds new variables and preserves existing ones; `transmute()` adds new variables and drops existing ones. New variables overwrite existing variables of the same name. Variables can be removed by setting their value to `NULL`.

Example:

```R
mutate(mtcars, displ_l = disp / 61.0237)
```

Warning: 

**It is always advisable to save your data using the <- assignment into a new data object** because `mutate()` does not directly modify the input dataframe. It leaves the input dataframe unchanged and then produces an output dataframe which is sent to the console by default (i.e., the console just prints the output).

```R
auto_specs_new <- mutate(auto_specs, hp_to_weight = horsepower / weight)
```
