Introduction to R language for beginners
================
He Ma
2022-09-27

## Function in R

This is an exercise for function in R. You can write your own functions
in order to make repetitive operations using a single command. Starting
by defining the function “my_function” and the input parameter(s) that
the user will feed to the function. Then define the operation that you
desire to program in the body of the function within curly braces ({}).
Finally, assign the result of the function in the return statement.

``` r
economist_scatter <- function(data, x, y, colour_by){
   
    { if (!is.data.frame(data)){
      stop("Can only compute dataframe.")
    }
 }     

    

library(ggthemes)
ggplot(data, aes(x = {{x}}, y = {{y}})) +
    geom_point(alpha = 0.5, size = 2, aes(colour = {{colour_by}})) +
    theme_economist()
   
}

economist_scatter(penguins, body_mass_g, flipper_length_mm, sex)
```

    ## Warning: Removed 2 rows containing missing values (geom_point).

![](Introduction-to-R-language-for-beginners_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

## Tidy data

This is an example for `fliter` and `select`. The tidyverse is an
opinionated collection of R packages designed for data science. All
packages share an underlying design philosophy, grammar, and data
structures. Filtering and selectiong data is one of the very basic
operation when you work with data.

``` r
dataset <-  tribble(
       ~name, ~alignment,  ~gender,          ~publisher,
   "Magneto",      "bad",   "male",            "Marvel",
     "Storm",     "good", "female",            "Marvel",
  "Mystique",      "bad", "female",            "Marvel",
    "Batman",     "good",   "male",                "DC",
     "Joker",      "bad",   "male",                "DC",
  "Catwoman",      "bad", "female",                "DC",
   "Hellboy",     "good",   "male", "Dark Horse Comics"
  )
dataset |> 
  filter(publisher == 'DC') |> 
  select(name:gender)  
```

    ## # A tibble: 3 × 3
    ##   name     alignment gender
    ##   <chr>    <chr>     <chr> 
    ## 1 Batman   good      male  
    ## 2 Joker    bad       male  
    ## 3 Catwoman bad       female
