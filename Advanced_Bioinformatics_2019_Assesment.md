---
title: "Advanced Bioinformatics 2019 Assesment"
author: "p1504814" 
output: 
  html_document:
    keep_md: true
---
Task 1:

```r
sum(5:55)
```

```
## [1] 1530
```
Task 2:

```r
sumfun <- function(n) {sum(5:n)}

sumfun(10)
```

```
## [1] 45
```

```r
sumfun(20)
```

```
## [1] 200
```

```r
sumfun(100)
```

```
## [1] 5040
```
Task 3:


```r
Fibonacci_seq <- numeric(12)
Fibonacci_seq[1] <- 1
Fibonacci_seq[2] <- 1
for (i in 3:12) { 
   Fibonacci_seq[i] <- Fibonacci_seq[i-1]+Fibonacci_seq[i-2]
}
print("The first 12 numbers of the Fibonacci sequence are:")
```

```
## [1] "The first 12 numbers of the Fibonacci sequence are:"
```

```r
print(Fibonacci_seq)
```

```
##  [1]   1   1   2   3   5   8  13  21  34  55  89 144
```

Task 4:

```r
library(ggplot2)

Gears <- as.factor((mtcars[,10]))


ggplot(mtcars, aes(x=Gears, y=mpg, color=Gears))+ 
geom_boxplot()+
scale_color_brewer(palette="BuPu")
```

![](Advanced_Bioinformatics_2019_Assesment_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

Task 5: 

```r
distance<-lm(dist~speed,cars)
summary(distance)
```

```
## 
## Call:
## lm(formula = dist ~ speed, data = cars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -29.069  -9.525  -2.272   9.215  43.201 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept) -17.5791     6.7584  -2.601   0.0123 *  
## speed         3.9324     0.4155   9.464 1.49e-12 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 15.38 on 48 degrees of freedom
## Multiple R-squared:  0.6511,	Adjusted R-squared:  0.6438 
## F-statistic: 89.57 on 1 and 48 DF,  p-value: 1.49e-12
```
Intercept= -17.5791, slope= 3.9324, standard deviation= 0.4155(speed) and 6.7584(dist)

Task 6:


```r
plot(cars, col='lightskyblue',pch=20, cex=2, main="Relationship between Speed and Stopping Distance ", "Speed (mph)", "Stopping Distance (feet)")
abline(-17.5791, 3.9324)
```

![](Advanced_Bioinformatics_2019_Assesment_files/figure-html/unnamed-chunk-6-1.png)<!-- -->
Task 7:

```r
new_speed <- cars$speed * (5280/3600)

line<-lm(dist ~ 0+ new_speed + I(new_speed^2),cars)


summary(line)
```

```
## 
## Call:
## lm(formula = dist ~ 0 + new_speed + I(new_speed^2), data = cars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -28.836  -9.071  -3.152   4.570  44.986 
## 
## Coefficients:
##                Estimate Std. Error t value Pr(>|t|)   
## new_speed       0.84479    0.38180   2.213  0.03171 * 
## I(new_speed^2)  0.04190    0.01366   3.067  0.00355 **
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 15.02 on 48 degrees of freedom
## Multiple R-squared:  0.9133,	Adjusted R-squared:  0.9097 
## F-statistic: 252.8 on 2 and 48 DF,  p-value: < 2.2e-16
```



Yes we get reasonable results. 0.84479 is a realistic average reaction speed.




```r
y <- cars$dist
x <- cars$new_speed

ggplot(cars,aes(new_speed,dist)) + 
    geom_point() + 
    geom_smooth(method="lm", formula="y~0+x+I(x^2)")
```

![](Advanced_Bioinformatics_2019_Assesment_files/figure-html/unnamed-chunk-8-1.png)<!-- -->

