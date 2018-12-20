Chapter 3 Notes
================
M Hannum
Sys.Date()

-   [Chapter 3: Subsetting](#chapter-3-subsetting)
    -   [Examples for quiz](#examples-for-quiz)

Chapter 3: Subsetting
=====================

Three subsetting operators:

Six types of subsetting:

Examples for quiz
-----------------

1.  Result of subsetting a vector with positive integers, negative integers, logical vector, or a character vector

``` r
df <- data.frame(x = c(1:3), y = c("a", "b", "c"))

#keep elements
df[1,]
```

    ##   x y
    ## 1 1 a

``` r
#drop elements
df[-1,]
```

    ##   x y
    ## 2 2 b
    ## 3 3 c

``` r
#keep TRUE elements
df[c(TRUE, TRUE, FALSE),]
```

    ##   x y
    ## 1 1 a
    ## 2 2 b

``` r
#keep elements with matching names
df[,"y"]
```

    ## [1] a b c
    ## Levels: a b c

1.  Difference between \[, \[\[, and $ when applied to a list

``` r
df2 <- data.frame(z = c(4:6))
l1 <- list(df = df, df2 = df2)

#returns a list
str(l1["df"])
```

    ## List of 1
    ##  $ df:'data.frame':  3 obs. of  2 variables:
    ##   ..$ x: int [1:3] 1 2 3
    ##   ..$ y: Factor w/ 3 levels "a","b","c": 1 2 3

``` r
#returns element in a list
str(l1[["df"]])
```

    ## 'data.frame':    3 obs. of  2 variables:
    ##  $ x: int  1 2 3
    ##  $ y: Factor w/ 3 levels "a","b","c": 1 2 3

``` r
#equivalent to [[]]
str(l1$df)
```

    ## 'data.frame':    3 obs. of  2 variables:
    ##  $ x: int  1 2 3
    ##  $ y: Factor w/ 3 levels "a","b","c": 1 2 3

1.  Use `drop = FALSE` when subsetting inside a function - WHY?

2.  What does `x[] <- 0` do to a matrix `x`?

``` r
x <- c(1:12)
dim(x) <- c(3,4)

x
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    4    7   10
    ## [2,]    2    5    8   11
    ## [3,]    3    6    9   12

``` r
#Make subset element of matrix 0 
x[1,1] <- 0

x
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    0    4    7   10
    ## [2,]    2    5    8   11
    ## [3,]    3    6    9   12

``` r
#makes every element of the matrix 0
x[] <- 0 

x
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    0    0    0    0
    ## [2,]    0    0    0    0
    ## [3,]    0    0    0    0
