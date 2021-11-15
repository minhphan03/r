## Normal Distribution

#####  pnorm(q,mean = 0,sd = 1,lower.tail=TRUE)

* By default, pnorm give $P(X\le x)$ assuming a normal distribution with $\mu=0$ and $\sigma=1$ 
* Do not need to convert to z-scores
* To use $P(X>x)$ change `lower.tail=FALSE`  

Ex: Assume that adults have IQ scores that are normally 
distributed with a mean of 100 and a SD of 15. For a 
randomly selected adult find:

a/ $P(X\le 130)$

```r
> pnorm(130, 100, 15)
[1]0.9772499
```

b/ $P(90\le X \le 100)$

```r
> pnorm(100,100,15) – pnorm(90,100,15) 
[1]0.2475075
```

##### qnorm(p,mean = 0,sd = 1,lower.tail = TRUE)

Ex: Assume that adults have IQ scores that are normally 
distributed with a mean of 100 and a SD of 15. For a 
randomly selected adult find:
a) Find the value of 𝑥 such that $P(X>x )=0.0643$ 

```r
qnorm(0.0643, 100, 15, lower.tail = FALSE)
[1] 122.7947
```

b) Find the value of 𝑥 such that $P(X\le x )=0.4500$

```r
qnorm(0.45, 100, 15, lower.tail = TRUE)
[1] 77.20531
```

 ##### rnorm(n, mean, sd)

* to generate n independent draws from a normal distribution with a given mean and 
  sd. The default is mean = 0 and sd = 1.



