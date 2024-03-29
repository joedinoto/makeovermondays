---
title: "Suicide_Stats"
author: "joedinoto"
date: "10/21/2019"
output: 
  html_document: 
    keep_md: yes
---




```r
# libraries 
library(tidyverse)
#install.packages("ggridges")
library(ggplot2)
library(ggridges)
```



```r
# Download the Data
url="https://www.ons.gov.uk/visualisations/dvc661/drugs/datadownload.csv"
suicide_stats <- readr::read_csv(url)
```

```
## Parsed with column specification:
## cols(
##   .default = col_double(),
##   Age = col_character()
## )
```

```
## See spec(...) for full column specifications.
```


```r
# reshape data into "tidy" format
suicide_stats_tidy <- suicide_stats %>% 
  gather("year","suicides",2:26)
```



```r
suicide_stats_tidy %>%
  ggplot(aes(x=suicides,y=year))+ 
  geom_density_ridges(scale=4,rel_min_height = 0.05)
```

```
## Picking joint bandwidth of 11.2
```

![](Suicide_Stats_files/figure-html/unnamed-chunk-4-1.png)<!-- -->


