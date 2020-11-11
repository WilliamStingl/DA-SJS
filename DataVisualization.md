DataVisualisation
================
William Stingl
8/21/2020

``` r
summary(cars)
```

    ##      speed           dist       
    ##  Min.   : 4.0   Min.   :  2.00  
    ##  1st Qu.:12.0   1st Qu.: 26.00  
    ##  Median :15.0   Median : 36.00  
    ##  Mean   :15.4   Mean   : 42.98  
    ##  3rd Qu.:19.0   3rd Qu.: 56.00  
    ##  Max.   :25.0   Max.   :120.00

# Data Visualization

### 3.1 Introduction

``` r
# load tidyverse library everyday

library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────────────────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.3     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.1     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ────────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

### 3.2 First Steps

QUESTIONS: Do cars with big engines use more gas than cars with small
engines?

###### 3.2.1 The mpg data frame

A data frame is a rectangular collection of variables (in the columns)
and observations (in the rows). mpg contains observations collected by
the US Environmental Protection Agency on 38 models of car.

``` r
mpg
```

    ## # A tibble: 234 x 11
    ##    manufacturer model    displ  year   cyl trans   drv     cty   hwy fl    class
    ##    <chr>        <chr>    <dbl> <int> <int> <chr>   <chr> <int> <int> <chr> <chr>
    ##  1 audi         a4         1.8  1999     4 auto(l… f        18    29 p     comp…
    ##  2 audi         a4         1.8  1999     4 manual… f        21    29 p     comp…
    ##  3 audi         a4         2    2008     4 manual… f        20    31 p     comp…
    ##  4 audi         a4         2    2008     4 auto(a… f        21    30 p     comp…
    ##  5 audi         a4         2.8  1999     6 auto(l… f        16    26 p     comp…
    ##  6 audi         a4         2.8  1999     6 manual… f        18    26 p     comp…
    ##  7 audi         a4         3.1  2008     6 auto(a… f        18    27 p     comp…
    ##  8 audi         a4 quat…   1.8  1999     4 manual… 4        18    26 p     comp…
    ##  9 audi         a4 quat…   1.8  1999     4 auto(l… 4        16    25 p     comp…
    ## 10 audi         a4 quat…   2    2008     4 manual… 4        20    28 p     comp…
    ## # … with 224 more rows

### 3.2.2 Creating a ggplot

``` r
ggplot(data=mpg) + geom_point(mapping = aes(x = displ, y = hwy))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

##### Excercises

1.  Run ggplot(data = mpg). What do you see?

<!-- end list -->

``` r
ggplot(data=mpg)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

2.  How many rows are in mpg? How many columns? 11

<!-- end list -->

``` r
?mpg
```

3.  What does the drv variable describe? Read the help for ?mpg to find
    out. drive

4.  Make a scatterplot of hwy vs cyl.

<!-- end list -->

``` r
ggplot(data=mpg) + geom_point(mapping = aes(x = cyl, y = hwy))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

5.  What happens if you make a scatterplot of class vs drv? Why is the
    plot not useful?

<!-- end list -->

``` r
ggplot(data=mpg) + geom_point(mapping = aes(x = class, y = drv))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

### 3.3 Aesthetic Mappings

``` r
ggplot(data=mpg) + geom_point(mapping = aes(x = displ, y = hwy, color=class))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy, size=class))
```

    ## Warning: Using size for a discrete variable is not advised.

![](DataVisualization_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy, alpha=class))
```

    ## Warning: Using alpha for a discrete variable is not advised.

![](DataVisualization_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ,y=hwy, shape=class))
```

    ## Warning: The shape palette can deal with a maximum of 6 discrete values because
    ## more than 6 becomes difficult to discriminate; you have 7. Consider
    ## specifying shapes manually if you must have them.

    ## Warning: Removed 62 rows containing missing values (geom_point).

![](DataVisualization_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy),color="blue")
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

###### 3.3.1 EXCERCISES

1.  What’s gone wrong with this code? Why are the points not blue?
    color=“blue” has to be outside the argument

<!-- end list -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy),color="blue")
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

2.  Which variables in mpg are categorical? Which variables are
    continuous? (Hint: type ?mpg to read the documentation for the
    dataset). How can you see this information when you run mpg? The
    variables that are categorical include characters, while the
    continuous variable are defined by integers and decimals.

<!-- end list -->

``` r
?mpg
```

3.  Map a continuous variable to color, size, and shape. How do these
    aesthetics behave differently for categorical vs. continuous
    variables?

<!-- end list -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy, color=cty))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy, size=cty))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

A continuous variable cannot be mapped to shape.

4.  What happens if you map the same variable to multiple aesthetics?
    redundant

<!-- end list -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy, color=hwy))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

5.  What does the stroke aesthetic do? What shapes does it work with?
    (Hint: use ?geom\_point)

6.  What happens if you map an aesthetic to something other than a
    variable name, like aes(colour = displ \< 5)? Note, you’ll also need
    to specify x and y.

<!-- end list -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy, color=displ<5))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

### 3.5 Facets

Inside of the sesthetic function the argument is about identifying the
variables then another other that can describe them.

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy))+facet_wrap(~class, nrow=2)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->
Facets are for categorical variables

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy))+facet_grid(drv~cyl)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

### 3.5.1 Excercises

1.  What happens if you facet on a continuous variable? Data becomes
    very murky and hard to understand. Without categories, adding
    another conitnuous varible muddles how useful the graph becomes.
    Good for identifying trends.

<!-- end list -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy))+facet_wrap(~cty, nrow=1)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->

2.  What do the empty cells in plot with facet\_grid(drv \~ cyl) mean?
    How do they relate to this plot? They represent the certain cars
    that are really produced. For example, 4 and 5-cylinder-rear wheel
    drive cars and 5 cylinder 4-wheel-drive cars are rare if not non
    existent.

<!-- end list -->

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=displ, y=hwy))+facet_grid(drv~cyl)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->

3.  What plots does the following code make? What does . do? When the
    decimal is on the right side of the facet\_grid argument the
    displ,hwy graph becomes organized by rows of the variable(drv) in
    the facet\_grid function.

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + facet_grid(drv ~ .)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-25-1.png)<!-- -->

When the decimal is on the left side of the facet\_grid argument the
displ,hwy graph becomes organized by columns of the variable(cyl) in the
facet\_grid function.

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + facet_grid(. ~ cyl)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-26-1.png)<!-- -->

4.Take the first faceted plot in this section: Faceting seems like r’s
way of arranging and specifying more unique data sets. If the graph is
paired with a categorical variable the data becomes more clear and
specified. Also, creating x amount of rows to model the position of the
graphs as well are an advantadge. However, graphs stacked on top of each
other lose the x axis counter, and data can become clustered up together
into black lumps, which can make distinguishing the data visually pretty
imprecise.

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + facet_wrap(~ class, nrow = 2)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-27-1.png)<!-- -->

5.  Read ?facet\_wrap. What does nrow do? What does ncol do? What other
    options control the layout of the individual panels? Why doesn’t
    facet\_grid() have nrow and ncol arguments?

nrow- number of rows to organize the data ncol- number of columns we
would like to organize the data by levels

``` r
?facet_wrap
```

6.  When using facet\_grid() you should usually put the variable with
    more unique levels in the columns. Why?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + facet_grid(cyl~cty)
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-29-1.png)<!-- -->

### 3.6 Geometric Objects

``` r
ggplot(data=mpg)+geom_smooth(mapping = aes(x=displ, y=hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-30-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy, linetype = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-31-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy, group = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-32-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy, color = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-33-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + geom_smooth(mapping = aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-34-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, color = drv)) + geom_smooth(mapping = aes(x = displ, y = hwy, color = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-35-1.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + geom_point() + geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-36-1.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_point(mapping = aes(color = class)) + geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-37-1.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_point(mapping = aes(color = class)) + geom_smooth(data = filter(mpg, class == "subcompact"), se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-38-1.png)<!-- -->

1.  What geom would you use to draw a line chart? A boxplot? A
    histogram? An area chart?

geom\_abline is horizontal, vertical, and diagonal, geom\_boxplot,
geom\_freqpoly, geom\_area

``` r
??geom 
```

2.  Run this code in your head and predict what the output will look
    like. Then, run the code in R and check your predictions.

se=False takes out the error parameters around the line graph.

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + geom_point() + geom_smooth(se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-40-1.png)<!-- -->

3.  What does show.legend = FALSE do? What happens if you remove it? Why
    do you think I used it earlier in the chapter?

Show.legend = FALSE removes the legend on the side of the graph. Focus
more on the graph.

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy, color = drv), show.legend = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-41-1.png)<!-- -->

4.  What does the se argument to geom\_smooth() do? it just adds and
    removes the error parameters

<!-- end list -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + geom_point() + geom_smooth(se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-42-1.png)<!-- -->

5.  Will these two graphs look different? Why/why not? No, because you
    are telling the program to fill in the empty brackets with the
    previous or subsequent arguments, which in this case is “data = mpg,
    mapping = aes(x = displ, y = hwy.”

<!-- end list -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point() + 
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-43-1.png)<!-- -->

``` r
ggplot() + 
  geom_point(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_smooth(data = mpg, mapping = aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](DataVisualization_files/figure-gfm/unnamed-chunk-43-2.png)<!-- -->

### 3.7 Statistical transformation

``` r
diamonds
```

    ## # A tibble: 53,940 x 10
    ##    carat cut       color clarity depth table price     x     y     z
    ##    <dbl> <ord>     <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1 0.23  Ideal     E     SI2      61.5    55   326  3.95  3.98  2.43
    ##  2 0.21  Premium   E     SI1      59.8    61   326  3.89  3.84  2.31
    ##  3 0.23  Good      E     VS1      56.9    65   327  4.05  4.07  2.31
    ##  4 0.290 Premium   I     VS2      62.4    58   334  4.2   4.23  2.63
    ##  5 0.31  Good      J     SI2      63.3    58   335  4.34  4.35  2.75
    ##  6 0.24  Very Good J     VVS2     62.8    57   336  3.94  3.96  2.48
    ##  7 0.24  Very Good I     VVS1     62.3    57   336  3.95  3.98  2.47
    ##  8 0.26  Very Good H     SI1      61.9    55   337  4.07  4.11  2.53
    ##  9 0.22  Fair      E     VS2      65.1    61   337  3.87  3.78  2.49
    ## 10 0.23  Very Good H     VS1      59.4    61   338  4     4.05  2.39
    ## # … with 53,930 more rows

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-45-1.png)<!-- -->

### 3.8 Position Adjustments

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, color = cut))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-46-1.png)<!-- -->

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-47-1.png)<!-- -->

``` r
ggplot(data=diamonds) + geom_bar(mapping = aes(x = cut, fill = clarity))
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-48-1.png)<!-- -->

``` r
ggplot(data = diamonds, mapping = aes(x = cut, fill = clarity)) + geom_bar(alpha = .2, position = "identity")
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-49-1.png)<!-- -->

``` r
ggplot(data = diamonds, mapping = aes(x = cut, colour = clarity)) + geom_bar(fill = NA, position = "identity")
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-50-1.png)<!-- -->

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = clarity), position = "fill")
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-51-1.png)<!-- -->

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = clarity), position = "dodge")
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-52-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy), position = "jitter")
```

![](DataVisualization_files/figure-gfm/unnamed-chunk-53-1.png)<!-- -->

# 3.8.1 Excercises

Notebook Check - exercises & notes

Project - start next week due after
