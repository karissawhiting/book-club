Chapter 2 Notes
================
M Hannum
2018-12-20

-   [Chapter 2: Structures Exercises](#chapter-2-structures-exercises)
    -   [2.1.3](#section)
    -   [2.2.2](#section-1)
    -   [2.3.1](#section-2)
    -   [2.4.5 Data frames](#data-frames)
    -   [Notes:](#notes)

Chapter 2: Structures Exercises
===============================

2.1.3
-----

1.  6 types of atomic vector: logical, integer, numeric (double), character, complex, and raw List differs from atomic vector in that it is recursive (can contain other lists).

2.  `is.vector()` and `is.numeric()` test specific things: `is.vector()` returns TRUE if x is a vector of the specified mode having no attributes other than names. `is.numeric()` returns TRUE for both numeric and integer. Different to `is.list()` and `is.character()` which return TRUE only if the objects tested are list or character respectively.

3.  Vector coercion rules: least to most flexible: Logical, integer, double, character

``` r
c(1, F) 
```

    ## [1] 1 0

``` r
c("a", 1)
```

    ## [1] "a" "1"

``` r
c(list(1), "a") 
```

    ## [[1]]
    ## [1] 1
    ## 
    ## [[2]]
    ## [1] "a"

``` r
c(TRUE, 1L)
```

    ## [1] 1 1

1.  `as.vector` just coerces argument into vector of specified mode (??)

2.  R automatically coerces elements to most convenient thing when possible. `1 == "1"` is T because it coerces 1 to "1" `-1 < FALSE` is T because it coerces FALSE to 0 `"one" < 2` is F because it coerces "2" to be a character, and number characters are evaluated as befor alphabetic ones

3.  Why is default missing value, NA, a logical vector? ??

2.2.2
-----

1.  `structure(1:5, comment = "my attribute")` doesn't print an attribute because a comment is a type of attribute that is not printed by default. Have to do `comment(x)` to print the comment.

2.  when you modify levels, it changes the entire printed output to revers Along with reversing the levels

``` r
f1 <- factor(letters)
f1
```

    ##  [1] a b c d e f g h i j k l m n o p q r s t u v w x y z
    ## Levels: a b c d e f g h i j k l m n o p q r s t u v w x y z

``` r
levels(f1) <- rev(levels(f1))
f1
```

    ##  [1] z y x w v u t s r q p o n m l k j i h g f e d c b a
    ## Levels: z y x w v u t s r q p o n m l k j i h g f e d c b a

1.  

``` r
#Reverses printout of factor while keeps levels a-z
f2 <- rev(factor(letters))
f2
```

    ##  [1] z y x w v u t s r q p o n m l k j i h g f e d c b a
    ## Levels: a b c d e f g h i j k l m n o p q r s t u v w x y z

``` r
f3 <- factor(letters, levels = rev(letters))
#Just reverses the levels, doesn't change order of factors
f3
```

    ##  [1] a b c d e f g h i j k l m n o p q r s t u v w x y z
    ## Levels: z y x w v u t s r q p o n m l k j i h g f e d c b a

2.3.1
-----

1.  `dim()` returns `NULL` when applied to a vector because it has no dimension

2.  `is.array()` returns TRUE for a matrix since a matrix is a 1d array

3.  

``` r
x1 <- array(1:5, c(1, 1, 5))
x2 <- array(1:5, c(1, 5, 1))
x3 <- array(1:5, c(5, 1, 1))
```

These three are 3d arrays with varying dimensions, which makes them different from 1:5.

2.4.5 Data frames
-----------------

1.  Attributes of a data frame: `names()`, `rownames()`, `class()`, and any custom ones

2.  `as.matrix()` will coerce different types of data into the least flexible type (e.g. it will make a character matrix) Since a matrix is only of one type of data but a df can be many types.

3.  You can have a data frame with 0 rows and zero columns

``` r
x4 <- data.frame(x = NULL)
x4
```

    ## data frame with 0 columns and 0 rows

Notes:
------

**Note** Factors = integer vectors with special class and attributes!

S3 object: list with class attribute set to a class name

`I()` treat an object "as is" (e.g. protecting lists or matrices which are to be added to a data fram)
