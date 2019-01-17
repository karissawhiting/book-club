Chapter 4 Notes
================
M Hannum
2018-12-31

-   [Chapter 4: Vocabulary](#chapter-4-vocabulary)
-   [Notes](#notes)

Chapter 4: Vocabulary
=====================

`<<-` I didn't know what this was, but [Hadley has a nice answer on stackoverflow](https://stackoverflow.com/questions/2628621/how-do-you-use-scoping-assignment-in-r). Brief summary: "Unlike the usual single arrow assignment (`<-`) that always works on the current level, the double arrow operator can modify variables in parent levels." This [CRAN article on scoping](https://cran.r-project.org/doc/manuals/R-intro.html#Scope) says, "For most users `<<-` creates a global variable and assigns the value of the right hand side to it. Only when `<<-` has been used in a function that was returned as the value of another function will the special behavior occur."

``` r
x <- 1
myfun <- function() {
  x <<- 3
  y <<- 4
  z <- 5
  return(x + y + z)
}

print(myfun())
#> [1] 12
x
#> [1] 3
y
#> [1] 4
z
#> Error in eval(expr, envir, enclos): object 'z' not found
```

`%%` gives remainder `%/%` gives quotiant

`xor` "indicates elementwise exclusive OR"

Discussion: Examples of using `sweep, diag`

`replicate` "wrapper for common use of `sapply` for repeated eval of an expression"

`trimws` to trim whitespace around character vector

Are `sink` and `capture.output` mainly for non-RStudio R use? Does anybody try to capture output in non-report form, for future use? (E.g. what if libraries used for analysis become outdated later and you want a record of output?)

Does anyone use the I/O functions about creating files within R? Any advantage over command line?

Notes
=====

Does the group prefer `stringr` over base regex pattern-matching functions?
