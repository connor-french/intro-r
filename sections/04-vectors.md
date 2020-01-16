04-vectors
================

[\<\<\< Previous](03-objects.md) | [Next \>\>\>](05-data-types.md)

# What is a vector?

A vector in R is a basic data structure with an one-dimensional array,
that is, it contains elements of the same type. The data types can
include logical (e.g. yes/no), chracters (e.g. “apple”, “ball”), and
intergers (e.g. “3”, “999”) amongst others. One of the property of a
vector is its length, and length is basically the number of elements in
the vector. A vector can have a single element or multiple elements, and
you can find the length of the vector, i.e. the number of elements in
the vector with the function `length()`.

The length of the vector `10` is 1 because there is only 1 element in
this vector, while the length of the vector

``` r
rnorm(10)
```

    ##  [1] -0.05801767  1.32317303  0.94098090 -0.03166799 -1.26227826
    ##  [6]  1.30931820  0.63066943  0.75101261  0.51698501 -1.49514487

is 10 because it has 10 elements in this vector.

## c() function

`c()` function helps to combine the values specified within the
parenthesis into a vector. This can be very useful for creating data
sets or when applying the same function on a series of elements. Note
that all elements in the vectors have to be of the same type; if they
are different, this function will attempt to coerce them into the same
elements.

``` r
b <- c(1, 2, 3, 4)
fruits <- c("pear", "apple", "banana", "melon")
b
```

    ## [1] 1 2 3 4

``` r
fruits
```

    ## [1] "pear"   "apple"  "banana" "melon"

You can also assign each value a name when creating your vectors.

``` r
c <- c(pop = 10, soda = 20, cola = 30)
c
```

    ##  pop soda cola 
    ##   10   20   30

Try and figure out what the following do before running them in R. If
you don’t know what type of data is in your vector, how might you be
able to find out?

``` r
c(1:10)
typeof(fruits)
```

## Functions that use vectors

Some functions require vectors. For example, the `mean()` function
computes the mean of a vector and the `sum()` computes the total.

``` r
mean(b)
```

    ## [1] 2.5

``` r
sum(b)
```

    ## [1] 10

### Vectorised functions

Many R functions will also take on a vector input. This tells R to apply
the function separately onto each element in the input and return the
results as a new vector (which you can also save into a new object as we
learned from the previous section).

``` r
factorial(b)
```

    ## [1]  1  2  6 24

You can apply some functions to multiple vectors, and R will apply the
function to each vector’s elements in order until it reaches the end of
the vector.

``` r
vec<-c(1,2,3,4,5)
vec2<-c(4,3,2,6,8)
pmax(vec, vec2)
```

    ## [1] 4 3 3 6 8

What do you think will happen when you do this:

``` r
10+vec2
```

Let’s try a quick exercise to practice and familiarize ourselves with
the R codes so far\! Try creating a vector with 5 elements, apply a
function on it, and save the results into a new object.

## Locating an element in a vector

What happens if you wanted to look for a specific element in a vector
that has multiple elements? You could use `[]` to help you locate and
extract that element in a specific vector. You can also specify multiple
extractions using the `c()` function within `[]`.

``` r
z <- c(1:5, 23, 34:57)
z[17] #this is telling R to look for the 17th element in the vector z and to return that result, which in this case is the number 44.
```

    ## [1] 44

``` r
z[c(1,7,26)] #can you explain what this is doing?
```

    ## [1]  1 34 53

If you have a name for your elements, you can also specify the
extraction using its name. Can you try to extract the element named cola
in the vector c?

``` r
c <- c(pop = 10, soda = 20, cola = 30)
```

# Writing your own function

Now that we have gone over some of the basic components in a piece of R
code, let’s try to write a function\! This is not as intimidating or
scary as it seems, and can be very useful as it can be made very
specific to your data set.

In writing your own function, it follows a fairly standard template
\[1\]

``` r
function.name <- function(arg1, arg2, arg3=2) {
  newVar <- sum(arg1) + sum(arg2)  # do some useful stuff
  return(newVar / arg3) # returns value 
}
```

`function.name` is the name of the funciton you’re creating. Name it
something that is easy to remember but does not clash with existing
functions in base R packages such as `mean()` or `sum()`.

`arg1` are arguments for the function you are defining. Much like the
arguments of the functions you called in [Functions](02-functions.md),
it can be any R object such as numbers, vectors, and data frames. In
this template, `arg3` has a default of 2, which makes it an option
argument when you call and apply the function.

`{}` is called the function body and it specifies the code that will run
when the function is called and applied. When writing your own function,
try to be as short as you can. Remember, functions are to help make your
work run more efficiently\! In the example above, the code is creating a
new variable, `newVar` that is the result of the sums of `arg1` and
`arg2` and than dividing `newVar` by `arg3` as the result for this
function.

`return` is the last line of code that will return the value of the
function. Remember this last line of *code* is written within the `{}`\!

## Practice\! Let’s make a mean function\!

Using what we have learnt so far, can you attempt to create a function
to find the mean of a vector? Think about the components that is needed
to find a mean from a set of numbers. Hint:
\[mean = \frac{sum of terms}{no. ofterms}\]

# Matrices

Matrices are not too different from vectors. All it has that is
different is an added dimensionality; it has rows and columns. The
arguments `nrow` and `ncol` are important to the creation of a matrix as
it specifies the desired number of rows and columns the matrix will take
on. Specifying one of the arguments is sufficient for the arrangement.

``` r
ma1 <- matrix(1:9, nrow = 3, ncol = 3) #is the same as
ma2 <- matrix(1:9, nrow = 3)
ma1
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    4    7
    ## [2,]    2    5    8
    ## [3,]    3    6    9

``` r
ma2
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    4    7
    ## [2,]    2    5    8
    ## [3,]    3    6    9

## Naming rows and columns

You could name your rows and columns as you are creating the matrix or
after the matrix is
created.

``` r
ma1 <- matrix(1:9, nrow = 3, dimnames = list(c("a","b","c"), c("x","y","z")))
ma1
```

    ##   x y z
    ## a 1 4 7
    ## b 2 5 8
    ## c 3 6 9

``` r
colnames(ma2) <- c("x","y","z")
ma2
```

    ##      x y z
    ## [1,] 1 4 7
    ## [2,] 2 5 8
    ## [3,] 3 6 9

Try changing the row names of ma2\!

## Creating a matrix from vectors

You can create a matrix from a vector by specifying its dimensions
(i.e. its rows and columns) using `dim()`.

``` r
vec3 <- c(5,6,3,7,7,3,7,9)
vec3
```

    ## [1] 5 6 3 7 7 3 7 9

``` r
dim(vec3) <- c(2,4)
vec3
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    5    3    7    7
    ## [2,]    6    7    3    9

You can also use the functions rowbind, `rbind()`, or column bind,
`cbind`, to place two vectors into a matrix.

``` r
x <- c(5, 3, 7, 7)
y <- c(6, 7, 3, 9)

#Which function could you use to get the same matrix as vec3?
```

Possible solution to writing a function exercise:

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

[\<\<\< Previous](03-objects.md) | [Next \>\>\>](05-data-types.md)  
[Glossary](glossary.md)

1.  Modified template from [Nice R
    Code](https://nicercode.github.io/guides/functions/)
