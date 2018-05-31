Exploring ggplot
================

``` r
library(ggplot2)
library(tidyverse)
```

    ## -- Attaching packages ------------------------------------------------------------ tidyverse 1.2.1 --

    ## v tibble  1.4.2     v purrr   0.2.4
    ## v tidyr   0.8.0     v dplyr   0.7.5
    ## v readr   1.1.1     v stringr 1.3.0
    ## v tibble  1.4.2     v forcats 0.3.0

    ## -- Conflicts --------------------------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
head(mpg)
```

    ## # A tibble: 6 x 11
    ##   manufacturer model displ  year   cyl trans drv     cty   hwy fl    class
    ##   <chr>        <chr> <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
    ## 1 audi         a4      1.8  1999     4 auto~ f        18    29 p     comp~
    ## 2 audi         a4      1.8  1999     4 manu~ f        21    29 p     comp~
    ## 3 audi         a4      2    2008     4 manu~ f        20    31 p     comp~
    ## 4 audi         a4      2    2008     4 auto~ f        21    30 p     comp~
    ## 5 audi         a4      2.8  1999     6 auto~ f        16    26 p     comp~
    ## 6 audi         a4      2.8  1999     6 manu~ f        18    26 p     comp~

``` r
#displacement vs highway
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-1.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=hwy,y=cyl))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-2.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=class,y=drv))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-3.png)

``` r
#displacement vs highway with color as class
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, color = class))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-4.png)

``` r
#displacement vs highway with size as class
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, size = class))
```

    ## Warning: Using size for a discrete variable is not advised.

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-5.png)

``` r
#displacement vs highway with color gradient as class
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, alpha = class))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-6.png)

``` r
#displacement vs highway with shape as class
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, shape = class))
```

    ## Warning: The shape palette can deal with a maximum of 6 discrete values
    ## because more than 6 becomes difficult to discriminate; you have 7.
    ## Consider specifying shapes manually if you must have them.

    ## Warning: Removed 62 rows containing missing values (geom_point).

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-7.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy) , color = "red")
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-8.png)

``` r
#shapes range from 0 - 20
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy) , shape = 4)
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-3-9.png)

``` r
#displacement vs highway with color as class
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, color = cty))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-4-1.png)

``` r
#displacement vs highway with size as class
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, size = cty))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-4-2.png)

``` r
#displacement vs highway with color gradient as class
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, alpha = cty))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-4-3.png)

``` r
#multiple aesthetics
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy, size = cty, color = class,shape=drv))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-5-1.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy) , shape = 13, stroke = 0.1)
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-6-1.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy,color=displ<5))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-7-1.png)

``` r
#adding facets
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy) , shape = 1)+
  facet_wrap(~class , nrow=2)
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-8-1.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy) , shape = 1)+
  facet_grid(drv~cyl)
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-9-1.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ,y=hwy) , shape = 1)+
  facet_grid(.~cyl)
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-10-1.png)

``` r
ggplot(data = mpg)+
  #geom_point(mapping = aes(x = displ,y = hwy))
  geom_smooth(mapping = aes(x = displ,y = hwy))
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-11-1.png)

``` r
ggplot(data = mpg)+
  #geom_point(mapping = aes(x = displ,y = hwy))
  geom_smooth(mapping = aes(x = displ,y = hwy, linetype = drv))
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-12-1.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x = displ,y = hwy,color=drv))+
  geom_smooth(mapping = aes(x = displ,y = hwy, linetype = drv))
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-13-1.png)

``` r
ggplot(data = mpg)+
  geom_smooth(mapping = aes(x = displ,y = hwy))
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-14-1.png)

``` r
ggplot(data = mpg)+
  geom_smooth(mapping = aes(x = displ,y = hwy, linetype = drv, group = drv))
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-14-2.png)

``` r
ggplot(data = mpg)+
  geom_smooth(mapping = aes(x = displ,y = hwy, color=drv))
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-14-3.png)

``` r
ggplot(data = mpg)+
  geom_point(mapping = aes(x=displ, y=hwy))+
  geom_smooth(mapping = aes(x=displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-15-1.png)

``` r
ggplot(data=mpg,mapping = aes(x=displ,y=hwy))+
  geom_point()+
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-16-1.png)

``` r
ggplot(data=mpg,mapping = aes(x=displ,y=hwy))+
  geom_point(mapping = aes(color=class))+
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-17-1.png)

``` r
ggplot(data=mpg,mapping = aes(x=displ,y=hwy))+
  geom_point(mapping = aes(color = class))+
  geom_smooth(data = filter(mpg, class == "subcompact"),se=FALSE) # SE - standard error
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-18-1.png)

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + 
  geom_point(show.legend = FALSE) + 
  geom_smooth(se = FALSE,show.legend = FALSE)
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-19-1.png)

``` r
ggplot(data = mpg) +
  geom_smooth(
    mapping = aes(x = displ, y = hwy, color = drv)
  )
```

    ## `geom_smooth()` using method = 'loess'

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-20-1.png)

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(mapping = aes(color=drv))
```

![](exploring_ggplot_mpg_files/figure-markdown_github/unnamed-chunk-21-1.png)
