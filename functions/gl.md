## gl()

Used to generate factors by specifying the pattern of their levels

```R
gl(n, k, length = n*k, labels = seq_len(n), ordered = FALSE)
```

in which: 

* n: number of levels
* k: number of replications

For example:

```R
# Creating a factor
# using gl() function
x1 <- gl(2, 5)
print(x1)
```

```R
 [1] 1 1 1 1 1 2 2 2 2 2
Levels: 1 2
```

```R
# gl() function with
# length and labels specified
x1 <- gl(3, 4, 12, label = letters[1:12])
```

```R
 [1] a a a a b b b b c c c c
Levels: a b c d e f g h i j k l
```

```R
# gl() function with
# length, label and order specified
x2 <- gl(3,4, 12, label = letters[1:12], ordered = T)
 
# Printing the factors
print(x1)
print(x2)
```

```R
 [1] a a a a b b b b c c c c
Levels: a < b < c < d < e < f < g < h < i < j < k < l
```

