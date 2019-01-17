Chapter 6 Notes
================
M Hannum
2018-12-31

-   [[Chapter 6: Functions](http://adv-r.had.co.nz/Functions.html)](#chapter-6-functions)
    -   [Function components](#function-components)

[Chapter 6: Functions](http://adv-r.had.co.nz/Functions.html)
=============================================================

**Opening quiz**

1.  3 components of a function: body, arguments, environment
2.  11 (comment: generally should functions within functions take input from the surrounding function? Haven't used the double ()() before)

``` r
x <- 10
f1 <- function(x) {
  function() {
    x + 10
  }
}
f1(1)()
```

    ## [1] 11

1.  `1 + (2 * 3)`

2.  

``` r
mean(c(1:10, NA), na.rm = TRUE)
```

    ## [1] 5.5

1.  `b` argument is never used in function so it does not stop or produce error message.

``` r
f2 <- function(a, b) {
  a * 10
}
f2(10, stop("This is an error!"))
```

    ## [1] 100

1.  infix function is binary operator function

Function components
-------------------

**6.1.2 Exercises**
1. Can use `class()` to tell if an object is a function. Can also use `is.function()` and `is.primitive()` for a logical test on if object is a function or primitive function.

1.  

<!-- -->

1.  The `scan()` function has the most arguments (22)

``` r
# make list of all functions in base package
objs <- mget(ls("package:base"), inherits = TRUE)
funs <- Filter(is.function, objs)

# find which base function has most arguments

# create a named vector of lengths
arg_length <- purrr::map_int(funs, function(x)(length(formals(x))))

#Get name of function with most arguments
max(arg_length)
```

    ## [1] 22

``` r
names(which(arg_length == max(arg_length)))
```

    ## [1] "scan"

1.  

``` r
no_args <- names(which(arg_length == 0))
head(no_args)
```

    ## [1] "-"   "!"   "!="  "$"   "$<-" "%%"

``` r
length(no_args)
```

    ## [1] 224

``` r
prims <- Filter(is.primitive, objs)
length(prims)
```

    ## [1] 183

``` r
arg_length_prims <- purrr::map_int(prims, function(x)(length(formals(x))))

non_prim_no_args <- no_args[!(no_args %in% names(prims))]

non_prim_no_args
```

    ##  [1] "closeAllConnections"      "contributors"            
    ##  [3] "Cstack_info"              "date"                    
    ##  [5] "default.stringsAsFactors" "extSoftVersion"          
    ##  [7] "getAllConnections"        "geterrmessage"           
    ##  [9] "getLoadedDLLs"            "getRversion"             
    ## [11] "getTaskCallbackNames"     "getwd"                   
    ## [13] "iconvlist"                "is.R"                    
    ## [15] "l10n_info"                "La_library"              
    ## [17] "La_version"               "libcurlVersion"          
    ## [19] "licence"                  "license"                 
    ## [21] "loadedNamespaces"         "loadingNamespaceInfo"    
    ## [23] "memory.profile"           "pcre_config"             
    ## [25] "R.Version"                "search"                  
    ## [27] "searchpaths"              "stderr"                  
    ## [29] "stdin"                    "stdout"                  
    ## [31] "sys.calls"                "Sys.Date"                
    ## [33] "sys.frames"               "Sys.getpid"              
    ## [35] "Sys.info"                 "Sys.localeconv"          
    ## [37] "sys.nframe"               "sys.on.exit"             
    ## [39] "sys.parents"              "sys.status"              
    ## [41] "Sys.time"

1.
