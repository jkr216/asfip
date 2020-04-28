 Reproducible Finance with R
========================================================
author: Jonathan Regenstein




Introducing R
========================================================

- Statistical programming language (C -> S -> R)
- Base + packages for analysis and vis
- Reproducible and intuitive

Financial Packages
========================================================

- PerformanceAnalytics
- PortfolioAnalytics
- TTR
- tidyquant
- quantmod
- xts

List of packages for finance here:
https://cran.r-project.org/web/views/Finance.html

Data Vis Packages
========================================================

- ggplot2 
- dygraphs
- highcharter
- plotly

Data Science Process: our philosophy 
================================================

![](tidyverse-paradigm.png)

Example Project: 5 ETFs
========================================================

- Import data for 5 ETFs
- Visualize prices and returns
_ Calculate some stats or interest 
- Create an SMA 50 v. SMA 200 chart.


We will work with price and returns data for 5 ETFS:

    + SPY (S&P500 fund)
    + IJS (a small-cap value fund) 
    + EEM (an emerging-mkts fund)


Import Data
========================================================

- Excel using `read_excel`
- yahoo! Finance using `getSymbols` or`tq_get`
- sql, or some internal database, using `dbConnect`


```r
symbols <- c("SPY", "IJS", "EEM")


etf_prices<-
  tq_get(symbols, from  = "2012-12-31") %>% 
  select(symbol, date, adjusted) %>% 
  spread(symbol, adjusted) %>% 
  tk_xts(date_var = date)
```

Quick look for sanity
==============================


```r
head(etf_prices)
```

```
                EEM      IJS      SPY
2012-12-31 39.63340 74.81863 127.7356
2013-01-02 40.41088 76.87150 131.0094
2013-01-03 40.12492 76.76980 130.7135
2013-01-04 40.20534 77.37086 131.2875
2013-01-07 39.90150 76.91773 130.9287
2013-01-08 39.54404 76.62183 130.5520
```

Base Plot
=====================================


```r
plot(etf_prices)
```

![plot of chunk unnamed-chunk-3](asfip-presentation-figure/unnamed-chunk-3-1.png)

Base Plot
=====================================





```
Error in loadNamespace(name) : there is no package called 'webshot'
```
