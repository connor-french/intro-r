03-objects
================

[\<\<\< Previous](02-functions.md) | [Next \>\>\>](04-vectors.md)

# Object structure

If you would like to use the results you got from running your codes,
you can save them on R by creating an object. To create an object, you
will first need to name what your object is going to be (something that
is easy to recall but not too lengthy) and then use the assignment
operator `<-` to store value in the object. R will store whatever is to
the right of the assignment operator into the named object on the left.

``` r
f <- log(45)
f
```

    ## [1] 3.806662

# Using objects

Whenever you call an object into your function and code, R will replace
the object with the value assigned to it and run said function and/or
code.

``` r
log(f)
```

    ## [1] 1.336753

# Watch out\! Overwriting values.

If you assign a new value into an existing object, you can
easily/accidentally overwrite the previous value in said object. R will
not hesitate to overwrite the value, giving you no warnings when you are
doing so. So, be careful and always double-check that the object doesn’t
already exist or you are sure in your intent to overwrite\!

``` r
a1 <- 45678
a1
```

    ## [1] 45678

``` r
a1 <- 98745
a1
```

    ## [1] 98745

Tutorial based off [R Studio
Primers](https://rstudio.cloud/learn/primers)

[\<\<\< Previous](02-functions.md) | [Next \>\>\>](04-vectors.md)  
[Glossary](glossary.md)
