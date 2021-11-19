## rep_sample_n()

Syntax:

```R
rep_sample_n(tbl, size, replace = FALSE, reps = 1, prob = NULL)
```

After applying the function, it will create a new column called replicate to keep track of what replication the data sampled is on (1st, 2nd, 3rd), which is convenient to perform further processing.

