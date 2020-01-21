Data structure
================

[\<\<\< Previous](04-vectors.md) | [Next \>\>\>](07-packages.md)

The primary data structures in R are vectors (which we’ve already
introduced), lists, and data frames. Data frames are the *de facto* way
to store tabular data, and are effectively a combination of vectors and
lists. Therefore, I’ll introduce the concept of a list first, then jump
right into data frames\!

# Lists

Lists are objects where you can store different data types. While
vectors only store a single data type, each “slot” in a list can contain
something different, and they can be almost arbitrarily complex.

Here’s an example:

``` r
list_data <- list("Bob", "Rachel", c(10, 2, 3), TRUE, FALSE, 22.4)

list_data
```

    ## [[1]]
    ## [1] "Bob"
    ## 
    ## [[2]]
    ## [1] "Rachel"
    ## 
    ## [[3]]
    ## [1] 10  2  3
    ## 
    ## [[4]]
    ## [1] TRUE
    ## 
    ## [[5]]
    ## [1] FALSE
    ## 
    ## [[6]]
    ## [1] 22.4

The `list()` function will create a list from just about anything\!

Here are the data types for each slot. This is a pretty flexible
structure\!

    ## [[1]]
    ## [1] "character"
    ## 
    ## [[2]]
    ## [1] "character"
    ## 
    ## [[3]]
    ## [1] "double"
    ## 
    ## [[4]]
    ## [1] "logical"
    ## 
    ## [[5]]
    ## [1] "logical"
    ## 
    ## [[6]]
    ## [1] "double"

If you know the numbered location of the slot you’re looking for, you
can access it using bracket indexing `[[]]`. For example, I’ve made a
list of character strings to represent a sentence.

``` r
my_list <- list("All", "dogs", "are", "good", "dogs")
```

I want to extract the word “good” from this list. I know it is in the
fourth slot, so I do this to access it:

``` r
my_list[[4]]
```

    ## [1] "good"

This is great, but what if you have a very long list, or complicated
list slots that makes accession by numbered indexing hard? Naming slots
within your lists helps with this\! It’s sometimes easier to remember
the names of slots, rather than their position in the list.

``` r
my_named_list <-
  list(
    char_vec = c("This", "is", "cool"),
    num_vec = c(12, 23, 44),
    log_vec = c(TRUE, FALSE, FALSE)
  )

my_named_list$char_vec
```

    ## [1] "This" "is"   "cool"

I was able to name each slot in the list using the structure `name =
contents` and access the slot using the structure `list_name$slot_name`.
`$` is a very useful operator that you’ll see again with data frames.

If you have a list with slots already and want to add names to them, you
can do that with the `names()` function\!

``` r
grocery_list <- list(12, 3, 6)

names(grocery_list) <- c("eggs", "potatoes", "bananas")

grocery_list
```

    ## $eggs
    ## [1] 12
    ## 
    ## $potatoes
    ## [1] 3
    ## 
    ## $bananas
    ## [1] 6

**Exercise 1**

You recorded the latitude/longitude coordinates of some of your favorite
restaurants, but forgot to name the list slots.

``` r
restaurant_list <-
  list(
    c(40.7594889, 40.7379186, 40.7467251),
    c(-73.9847482,-73.9814907,-73.9861467),
    c("Authentic Italian", "Authentic Mexican", "Best Deli")
  )

restaurant_list
```

    ## [[1]]
    ## [1] 40.75949 40.73792 40.74673
    ## 
    ## [[2]]
    ## [1] -73.98475 -73.98149 -73.98615
    ## 
    ## [[3]]
    ## [1] "Authentic Italian" "Authentic Mexican" "Best Deli"

It’s tough to remember which slot is latitude and which slot is
longitude, so you’d better name your slots while they’re fresh on your
mind.

1)  Name each list slot *latitude*, *longitude*, and *restaurant* in
    that order.

2)  You forgot whether you included the negative signs to indicate that
    the restaurants are in the western hemisphere. Access the
    *longitude* slot to double-check.

3)  What are the data types of each slot?

# Data frames

Data frames are tabular representations of data where the columns are
vectors of equal length. Each column must contain a single type of data
(remember, they’re vectors\!). Typically, you’ll either load in data
that is recorded in spreadsheet format (e.g. an Excel sheet), or you’ll
coerce non-tabular data into a data frame format (e.g. JSON files, which
aren’t natively represented as a table). R is optimized to use data
frames for statistical analysis and data visualization, so it’s
important you become familiar with them\!

![dataframe](/Users/connorfrench/Dropbox/Old_Mac/School_Stuff/CUNY/GCDI/intro-r/images/dataframe.png)

## Tidy data

Tidy data is tabular data, where each column is a *variable* and each
row is an *observation*. Tidy data looks like this:

    ## # A tibble: 15 x 5
    ##    frog_id   day plot_1 plot_2 plot_3
    ##    <chr>   <dbl>  <dbl>  <dbl>  <dbl>
    ##  1 FRE_1       1      0      1      0
    ##  2 FRE_2       1      0      1      0
    ##  3 FRE_3       1      0      0      1
    ##  4 FRE_4       1      0      0      0
    ##  5 FRE_5       1      1      0      0
    ##  6 FRE_1       2      0      1      0
    ##  7 FRE_2       2      0      0      0
    ##  8 FRE_3       2      0      0      0
    ##  9 FRE_4       2      0      0      0
    ## 10 FRE_5       2      0      0      0
    ## 11 FRE_1       3      0      1      0
    ## 12 FRE_2       3      0      1      0
    ## 13 FRE_3       3      0      1      0
    ## 14 FRE_4       3      1      0      1
    ## 15 FRE_5       3      0      0      0

This is a small (fake) data set from an experiment to estimate the
dispersal of frogs. I marked the identity of five frogs, released them,
and returned three times to three experimental plots to try to recapture
them (this is known as a “mark-recapture” experiment). Each time I
caught a frog I noted its identity, which day I found it, and which plot
it belonged to. Each *value* (or cell if you like thinking in terms of
an Excel spreadsheet) indicates if I observed the frog (0 for no
observation, 1 for observation). The variables are **frog\_id**,
**day**, and observation status for **plot\_1**, **plot\_2**, and
**plot\_3**. Note that there are no further ways to subdivide the data.

Below is the same data represented in an untidy format.

    ## # A tibble: 5 x 10
    ##   frog_id plot_1_day_1 plot_1_day_2 plot_1_day_3 plot_2_day_1 plot_2_day_2
    ##   <chr>          <dbl>        <dbl>        <dbl>        <dbl>        <dbl>
    ## 1 FRE_1              0            0            0            1            1
    ## 2 FRE_2              0            0            0            1            0
    ## 3 FRE_3              0            0            0            0            0
    ## 4 FRE_4              0            0            1            0            0
    ## 5 FRE_5              1            0            0            0            0
    ## # … with 4 more variables: plot_2_day_3 <dbl>, plot_3_day_1 <dbl>,
    ## #   plot_3_day_2 <dbl>, plot_3_day_3 <dbl>

This represents the format that the data was probably recorded in. A
column for plot-day combination for each frog is easier to read while in
the field than thumbing down a page for each frog-day pair. However, it
makes analysis difficult. It limits the number of ways you can summarize
the data. For instance you can’t look at the total number of frogs
observed in each plot, or the total number of frogs observed for each
day. **Tidy** data is standardized in a way that R can easily analyze.
**Messy** data is anything that deviates from this format.

Three common problems seen in messy data sets are:

  - Column headers are values, not variable names.

  - Multiple variables are stored in one column.

  - Variables are stored in both rows and columns.

**Exercise 2**

Which of the three common problems are seen in the **messy** data format
of the mark-recapture experiment?

Check out the
[tidyr](https://cran.r-project.org/web/packages/tidyr/vignettes/tidy-data.html)
documentation for a more in-depth discussion of tidy data. There’s more
nuance to the definition of tidy data than you’d think\!

### Tibbles

You may have noticed the above output contains a little section that
looks like this: `# A tibble: 15 x 5`. Tibbles are data frames that cut
out the extra fluff that the base R `data.frame` class adds to your data
structure (Run `?data.frame` to see exactly what R does under the hood
to your data). Tibbles also add a bit of useful information to your data
frame output. Let’s take another look at the frog mark-recapture data
set.

    ## # A tibble: 15 x 5
    ##    frog_id   day plot_1 plot_2 plot_3
    ##    <chr>   <dbl>  <dbl>  <dbl>  <dbl>
    ##  1 FRE_1       1      0      1      0
    ##  2 FRE_2       1      0      1      0
    ##  3 FRE_3       1      0      0      1
    ##  4 FRE_4       1      0      0      0
    ##  5 FRE_5       1      1      0      0
    ##  6 FRE_1       2      0      1      0
    ##  7 FRE_2       2      0      0      0
    ##  8 FRE_3       2      0      0      0
    ##  9 FRE_4       2      0      0      0
    ## 10 FRE_5       2      0      0      0
    ## 11 FRE_1       3      0      1      0
    ## 12 FRE_2       3      0      1      0
    ## 13 FRE_3       3      0      1      0
    ## 14 FRE_4       3      1      0      1
    ## 15 FRE_5       3      0      0      0

The heading tells you the dimensions of your data. In this case, 15 rows
by 5 columns. In addition, the data type of each variable is printed
under the variable name. Although the data set is small enough to print
the entire table to your console, tibbles will conveniently limit the
number of rows printed for easy viewing. Another convenient feature is
illustrated with our **messy** data set.

    ## # A tibble: 5 x 10
    ##   frog_id plot_1_day_1 plot_1_day_2 plot_1_day_3 plot_2_day_1 plot_2_day_2
    ##   <chr>          <dbl>        <dbl>        <dbl>        <dbl>        <dbl>
    ## 1 FRE_1              0            0            0            1            1
    ## 2 FRE_2              0            0            0            1            0
    ## 3 FRE_3              0            0            0            0            0
    ## 4 FRE_4              0            0            1            0            0
    ## 5 FRE_5              1            0            0            0            0
    ## # … with 4 more variables: plot_2_day_3 <dbl>, plot_3_day_1 <dbl>,
    ## #   plot_3_day_2 <dbl>, plot_3_day_3 <dbl>

If you have too many variables to fit in the console, it will list the
variable names and their data types under the printed table. This is
convenient for very large data sets.

You’ll learn how to make and manipulate tibbles in the Data Wrangling
workshop tomorrow, but I wanted to introduce them to you today since
you’ll be seeing them a lot.

## Answers

**Exercise 1**

1)  
<!-- end list -->

``` r
# the short way
names(restaurant_list) <- c("latitude", "longitude", "restaurant")
```

``` r
# the long way
restaurant_list <-
  list(
    latitude = c(40.7594889, 40.7379186, 40.7467251),
    longitude = c(-73.9847482,-73.9814907,-73.9861467),
    restaurant = c("Authentic Italian", "Authentic Mexican", "Best Deli")
  )
```

2)  
<!-- end list -->

``` r
# access by name
restaurant_list$longitude
```

    ## [1] -73.98475 -73.98149 -73.98615

``` r
# access by index
restaurant_list[[2]]
```

    ## [1] -73.98475 -73.98149 -73.98615

3)  
<!-- end list -->

``` r
typeof(restaurant_list$latitude)
## [1] "double"
typeof(restaurant_list$longitude)
## [1] "double"
typeof(restaurant_list$restaurant)
## [1] "character"
```

**Exercise 2** Multiple variables are stored in one column.

[\<\<\< Previous](04-vectors.md) | [Next \>\>\>](07-packages.md)  
