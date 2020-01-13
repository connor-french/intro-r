Functions and arguments
================

[\<\<\< Previous](01-introduction.md) | [Next \>\>\>](03-objects.md)

Note from Connor: I think the function that we have them construct
should just be their version of the `mean()` function.

``` r
take_avg <- function(x){
  
  # this function takes the same of all values in x. Assumes x is numerical
  s <- sum(x)
  
  # this counts the number of elements in x
  l <- length(x)
  
  # we're dividing the sum of values by the number of values to calculate the mean
  avg <- s / l
  
  # this specifies the value to be returned by the function
  return(avg)
}
```

# Functions

## Code body

## Run a function

## Help page

# Arguments

## args()

## Matching arguments

## Default arguments

[\<\<\< Previous](01-introduction.md) | [Next \>\>\>](03-objects.md)  
[Glossary](glossary.md)
