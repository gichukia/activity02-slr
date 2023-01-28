Activity 2 - Day 1
================

The hfi data set has 1458 rows and 123 variables. Each row represents a
countries data for a specific year.

### Exploring Data for 2016

Creating a scatter plot to evaluate the relationship between pf_score
and pf_expression_control. I plot Expression Control on the x axis since
it is the predictor variable.

``` r
ggplot(data = hfi_2016, aes(pf_expression_control, pf_score)) +
  geom_point(alpha = 0.5, size= 2) +
  labs(x = "Expression Control", y = "Score",
       title = "Scatter Plot for Expression Control and Score") 
```

![](activity02-day01_files/figure-gfm/scatter%20plot-1.png)<!-- -->

It looks like there could be a linear relationship in the scatter plot
and we could use a linear model to predict personal freedom score.

## Sum of Squared Residuals

``` r
# Using trial and Error

statsr::plot_ss(x = pf_expression_control, y = pf_score, data = hfi_2016, showSquares = TRUE)
```

![](activity02-day01_files/figure-gfm/Sum%20of%20Squared%20Residuals-1.png)<!-- -->

    ## Click two points to make a line.                                
    ## Call:
    ## lm(formula = y ~ x, data = pts)
    ## 
    ## Coefficients:
    ## (Intercept)            x  
    ##      4.2838       0.5418  
    ## 
    ## Sum of Squares:  102.213

It is not easy to get the correct least squares line using this method.
The least sum of squares I got was 278.852.

## The Linear Model

``` r
# Using lm function from base R to plot a regression line
m1 <- lm(pf_score ~ pf_expression_control, data = hfi_2016)

tidy(m1)
```

    ## # A tibble: 2 x 5
    ##   term                  estimate std.error statistic  p.value
    ##   <chr>                    <dbl>     <dbl>     <dbl>    <dbl>
    ## 1 (Intercept)              4.28     0.149       28.8 4.23e-65
    ## 2 pf_expression_control    0.542    0.0271      20.0 2.31e-45

From the code chunk above, the least squares regression line for the
model is y = 4.28 + 0.542(pf_expression_control)

The y intercept is 4.28 + 0.542(pf_expression_control) while the slope
of the line is 0.542
