## count()

```R
count(df, vars = NULL, wt_var = NULL)
```

Return a tibble (temporary table)

```R
df %>% count(a, b)
```

is roughly equivalent to 

```R
df %>% group_by(a, b) %>% summarise(n = n())
```

