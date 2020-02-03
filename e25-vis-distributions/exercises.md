Distributions
================
Your Name
2019-09-25

``` r
# Libraries
library(tidyverse)

# Parameters
  # File with ideology scores for US House of Representatives
file_ideology <- "../../data/congress/ideology_house.rds"

#===============================================================================

# Recent storms data
storms_recent <-
  storms %>% 
  filter(year > 2013)

# Ideology scores for US House of Representatives
ideology <- read_rds(file_ideology)
```

**q1** Use `theme()` to make the following adjustments to this plot:

  - Turn the plot background white
  - Turn both minor and major grid lines gray
  - Change the axis text to size 12

<!-- end list -->

``` r
storms_recent %>% 
  ggplot(aes(wind)) +
  geom_histogram(binwidth = 10)
```

![](exercises_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

**q2** The `storms_recent` data is a subset of the `dplyr::storms` data
that includes only recent storms. Use `storms_recent` to recreate the
following plots.

Note: For all plots, show your code.

**q2.1**

![](data/q2.1.png)<!-- -->

**q2.2**

![](data/q2.2.png)<!-- -->

**q3** Improve upon this `diamonds` plot that tried to visualize the
distribution of `carat` for different values of `cut`.

``` r
diamonds %>% 
  filter(carat < 2.5) %>% 
  ggplot(aes(carat, fill = cut)) + 
  geom_histogram(binwidth = 0.1) +
  scale_fill_discrete()
```

![](exercises_files/figure-gfm/q3-1.png)<!-- -->

**q4** `ideology` contains data on the ideological views for Democrat
and Republican members of the US House of Representatives from eight
different Congresses (1945, 1955, 1965, 1975, 1985, 1995, 2005, and
2015).

``` r
ideology %>% 
  slice(1:10) %>% 
  knitr::kable()
```

| congress | year | chamber | state | district | name                           | id      | party            |   score |
| -------: | ---: | :------ | :---- | -------: | :----------------------------- | :------ | :--------------- | ------: |
|       79 | 1945 | House   | AL    |        1 | BOYKIN, Frank William          | B000725 | Democratic Party | \-0.105 |
|       79 | 1945 | House   | AL    |        2 | GRANT, George McInvale         | G000381 | Democratic Party | \-0.117 |
|       79 | 1945 | House   | AL    |        3 | ANDREWS, George William        | A000206 | Democratic Party | \-0.030 |
|       79 | 1945 | House   | AL    |        4 | HOBBS, Samuel Francis          | H000663 | Democratic Party | \-0.176 |
|       79 | 1945 | House   | AL    |        5 | RAINS, Albert McKinley         | R000018 | Democratic Party | \-0.342 |
|       79 | 1945 | House   | AL    |        6 | JARMAN, Peterson Bryant (Pete) | J000058 | Democratic Party | \-0.238 |
|       79 | 1945 | House   | AL    |        7 | MANASCO, Carter                | M000094 | Democratic Party | \-0.146 |
|       79 | 1945 | House   | AL    |        8 | SPARKMAN, John Jackson         | S000701 | Democratic Party | \-0.204 |
|       79 | 1945 | House   | AL    |        9 | PATRICK, Luther                | P000105 | Democratic Party | \-0.371 |
|       79 | 1945 | House   | AR    |        1 | GATHINGS, Ezekiel Candler      | G000098 | Democratic Party |   0.012 |

`score` is the [NOMINATE first dimension
estimate](https://en.wikipedia.org/wiki/NOMINATE_\(scaling_method\)). A
`score` of -1 indicates that the member is extremely liberal, while a
`score` of 1 indicates that they are extremely conservative. The data is
available from [voteview.com](https://voteview.com/data).

**q4.1** Create three completely different EDA plots that show the
relationship between `year`, `party`, and `score`.

**q4.2** Choose your best plot from **q4.1** and turn it into a
presentation plot.

<!-- Use following chunk for plot. -->

<!-- notes-link -->
