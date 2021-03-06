---
title       : Stock Performance v. S&P500
subtitle    : The beginnings of a portfolio analysis tool
author      : KFollmer
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## The Purpose

The motivation for this Shiny app is to be able to compare how my personal stock portfolio compares against the S&P500. I use the application Robinhood, and don't understand why I can't compare my all time portfolio perforamnce. The only available option is the last year.

--- 

## How to Use

1. Type in a stock ticker of interest _(ex. 'GOOG', 'JNJ', 'CMG', 'V')_
2. Optional: Adjust start and end date to timerange of interest
3. Press 'Add to Portfolio' to update the graph

---


## Calculations Used

There are not very advanced calculations in this app at this time.

1. Price Adjustment - to get cumulative returns, we divide the price by the starting price to understand the change


```r
library(quantmod)
library(data.table)
from.dat <- as.Date("01-01-08", format = "%m-%d-%y")
to.dat <- Sys.Date()
getSymbols("SPY", from = from.dat, to = to.dat)
# By monthly detail only
mspy <- to.monthly(SPY)
# Closing prices only
cspy <- Cl(mspy)
# As numeric so that we get cumulative returns
dspy <- as.numeric(cspy[1])
spy <-cspy/dspy
```

---


## Future Improvements

Ideas for improvement:

1. When stocks are added they are cumulatively stored, and also a portfolio value is calculated.
2. Give the user the ability to select which index they are comparing to.
3. Give the user the ability to toggle between individal stocks in the portfolio or the portfolio created as a whole

---

## Reference

I very closely followed the tutotial found [here](http://blog.revolutionanalytics.com/2014/01/quantitative-finance-applications-in-r-plotting-xts-time-series.html) to make my graphic 

---




