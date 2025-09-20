Homework 1
================
Satya Batna
2025-09-20

# Load the dataset

``` r
data("early_january_weather")
```

This data set has 358 rows and 15 columns. This data is the hourly
temperature from EWR in 2013. The variables that are listed are origin,
year, day, time, hour, temp, dewp, humid, wind_dir, wind_speed,
wind_gust,precip, pressure, visib, and time_hour.With mean 39.5821229
degrees.

``` r
ggplot(early_january_weather, aes(x = time_hour, y = temp, color = humid)) +
  geom_point(alpha = 0.8) +
  labs(
    x = "Time (hours)",
    y = "Temperature (°F)",
    color = "Humidity",
    title = "EWR temperature across early January 2013"
  ) +
  theme_minimal()
```

![](Homework-1_files/figure-gfm/unnamed-chunk-2-1.png)<!-- --> This
scatterplot shows us the increasing in temperature over time and for
lower humidity we have higher temperatures.

``` r
ggsave ("scatter_plot.pdf", height = 4, width = 6)
```

\#Problem 2

set.seed(123)

``` r
set.seed(123)

df <- tibble(
  norm_sample = rnorm(10),                         
  is_positive = rnorm(10) > 0,                      
  char_vec    = sample(letters, 10),                
  fact_vec    = factor(sample(c("low", "med", "high"), 10, replace = TRUE))
)

df
```

    ## # A tibble: 10 × 4
    ##    norm_sample is_positive char_vec fact_vec
    ##          <dbl> <lgl>       <chr>    <fct>   
    ##  1     -0.560  TRUE        o        low     
    ##  2     -0.230  TRUE        j        low     
    ##  3      1.56   TRUE        m        high    
    ##  4      0.0705 TRUE        g        low     
    ##  5      0.129  FALSE       i        med     
    ##  6      1.72   TRUE        v        low     
    ##  7      0.461  TRUE        y        low     
    ##  8     -1.27   FALSE       w        high    
    ##  9     -0.687  TRUE        f        low     
    ## 10     -0.446  FALSE       b        med

``` r
mean(pull(df,norm_sample))
```

    ## [1] 0.07462564

``` r
mean(pull(df,is_positive))
```

    ## [1] 0.7

``` r
mean(pull(df,char_vec))
```

    ## Warning in mean.default(pull(df, char_vec)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(df,fact_vec))
```

    ## Warning in mean.default(pull(df, fact_vec)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA
