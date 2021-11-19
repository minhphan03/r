## group_by()

Syntax:

```r
group_by(.data, ..., .add = FALSE, .drop = group_by_drop_default(.data))
```

The use of `group_by()` function is very important in the extent of how a function (summarize, mutate) works in scopes (determined by the group_by() function itself)

Most data operations are done on groups defined by variables. `group_by()` takes an existing tbl and converts it into a grouped tbl where operations are performed "by group". `ungroup()` removes grouping.

Example:

```r
ZOD 
%>% rep_sample_n(size = nrow(ZOD), reps=1000, replace=FALSE) 
%>% mutate(ZOD_perm=sample(ZOD)) 
%>% group_by(replicate,Pie) 
%>% summarize(prop_ZOD_perm=mean(ZOD_perm), prop_ZOD = mean(ZOD)) 
%>% summarize(diff_perm = diff(prop_ZOD_perm), diff_org=diff(prop_ZOD)) 
```

After `rep_sample_n()`: there are 12000 rows (12 rows of the original ZOD table * 1000 replicates)

```r
# A tibble: 12,000 x 4
# Groups:   replicate [1,000]
   replicate Pie      ZOD ZOD_perm
       <int> <fct>  <dbl>    <dbl>
 1         1 Cherry   3        1  
 2         1 Cherry   7        2  
 3         1 Apple    1.5      5  
 4         1 Apple    2        5.5
 5         1 Apple    2        7  
 6         1 Apple    1        2  
 7         1 Apple    0.5      6.5
 8         1 Apple    0        0.5
 9         1 Cherry   5        1.5
10         1 Cherry   6.5      0  
# ... with 11,990 more rows
```

Using `group_by()` we have two levels - by replicate and type of pie in each replicate

After the first summarize: We have 2000 (1/6th of the original) rows: We summarize first by calculate the mean of the ZOD_perms by each pie in each replicate (6 pies each per type per replicate). 

```r
# A tibble: 2,000 x 4
# Groups:   replicate [1,000]
   replicate Pie    prop_ZOD_perm prop_ZOD
       <int> <fct>          <dbl>    <dbl>
 1         1 Apple           4.42     1.17
 2         1 Cherry          1.58     4.83
 3         2 Apple           3.25     1.17
 4         2 Cherry          2.75     4.83
 5         3 Apple           2.92     1.17
 6         3 Cherry          3.08     4.83
 7         4 Apple           4.17     1.17
 8         4 Cherry          1.83     4.83
 9         5 Apple           4.83     1.17
10         5 Cherry          1.17     4.83
# ... with 1,990 more rows
```

After the second summarize, since there are only two pies by each, the `diff()` function (which calculate the difference between two consecutive numbers in a vector (or in this case a column)) was only able to calculate one out of two because of the constraint in the `group_by()` function ($4.83 - 1.17$ of replicate 1, not $1.13 - 4.83 $ of the former in replicate 2 to the latter in replicate 1 ) Therefore, the number of rows was halved. 

```r
# A tibble: 1,000 x 3
   replicate diff_perm diff_org
       <int>     <dbl>    <dbl>
 1         1    -0.333     3.67
 2         2    -0.833     3.67
 3         3     0         3.67
 4         4     1.33      3.67
 5         5    -0.5       3.67
 6         6    -1         3.67
 7         7     0.5       3.67
 8         8    -2.17      3.67
 9         9     0.333     3.67
10        10     0.333     3.67
# ... with 990 more rows
```

