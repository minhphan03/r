### lm()

Used to produce linear regression by creating regression models, often givien in the form of ax + b

Use the `summary()` function to peek at the regression information.

For example

```R
simple.fit = lm(Sales~Spend, data=dataset)
summary(simple.fit)
multi.fit = lm(Sales~Spend+Month, data=dataset)
summary(multi.fit)
```

