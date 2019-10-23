---
title: "UK_life_expectancy"
author: "joedinoto"
date: "10/21/2019"
output: 
  html_document: 
    keep_md: yes
---




```r
# libraries
library(tidyverse)
```



```r
# obtain the data
url = "https://data.london.gov.uk/download/life-expectancy-birth-and-age-65-ward/38b6745f-168a-493d-9ff4-2b3ba63e86f2/life-expectancy-ward-at-Birth.csv"
UK_life_expentancy_original <- readr::read_csv(url)
```


```r
# Local authority, males, avg life expectancy, by year
UK_life_expentancy_small <- UK_life_expentancy_original %>%
  select(`Local Authority`,matches("(Male;Life)"), -matches("female")) 
```

```r
# rename column headers to only year
  names(UK_life_expentancy_small)[2:13] <- 1999:2010
unique(UK_life_expentancy_small$`Local Authority`) # number of unique Local Authorities
```

```
##  [1] "Barking and Dagenham"   "Barnet"                
##  [3] "Bexley"                 "Brent"                 
##  [5] "Bromley"                "Camden"                
##  [7] "Croydon"                "Ealing"                
##  [9] "Enfield"                "Greenwich"             
## [11] "Hackney"                "Hammersmith and Fulham"
## [13] "Haringey"               "Harrow"                
## [15] "Havering"               "Hillingdon"            
## [17] "Hounslow"               "Islington"             
## [19] "Kensington and Chelsea" "Kingston upon Thames"  
## [21] "Lambeth"                "Lewisham"              
## [23] "Merton"                 "Newham"                
## [25] "Redbridge"              "Richmond upon Thames"  
## [27] "Southwark"              "Sutton"                
## [29] "Tower Hamlets"          "Waltham Forest"        
## [31] "Wandsworth"             "Westminster, City of"  
## [33] "City of London"         NA
```

```r
sum(is.na(UK_life_expentancy_small$`Local Authority`)) # count of NAs
```

```
## [1] 12
```

```r
# Next step, boxplots for each of the 33 wards, average of lifespan by year
```


