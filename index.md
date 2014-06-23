---
title       : Segment Detection in Nike+ Pedometer Run Data
subtitle    : Final project for Developing Data Products
author      : Rick Osborne
job         : rickosborne.org
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : solarized_light      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- .hbottom

# I am _not_ that smooth.

When Nike+ tells me how fast I'm going it looks like this:

![Nike+ Run Data](assets/img/nike-chart.png)

---

# But I _can_ read XML data ...


```r
source('nikeplus.R')
plus <- read.nikePlus(file.path('xml', '2007-07-11 20;59;57.xml'))
head(plus@intervals[,c("distanceKM","durationMin","diffKM","speedKPH")])
```

```
##   distanceKM durationMin diffKM speedKPH
## 1     0.0000      0.0000     NA       NA
## 2     0.0130      0.1667 0.0130    4.680
## 3     0.0307      0.3333 0.0177    6.372
## 4     0.0505      0.5000 0.0198    7.128
## 5     0.0693      0.6667 0.0188    6.768
## 6     0.0864      0.8333 0.0171    6.156
```

---

# I can use linear models to find breakpoints.


```r
plotNike(plus@intervals, minimumPoints=5, windowSize=7, title=plus@time)
```

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2.png) 

--- .solo

# [ricko.is/shiny](http://ricko.is/shiny)
