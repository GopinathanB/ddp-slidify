---
title       : Drug Concentration Predictor
subtitle    : Developing Data Products
author      : Gopinathan Balaji
job         : Dec 2014
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : prettify      # {highlight.js, prettify, highlight}
hitheme     : twitter-bootstrap      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

### Presenting a Drug Concentration Predictor
- Given a dose (in milligrams) of the drug introduced to a Subject,
and the hours since the dose was introduced,
- Predicts the drug concentration in the blood system (as mg/L) at the
hour input.



--- .class #id 

## Input and Output

### Input
- Friendly sliders to input dose and hours. 
- Range and data type validated.

### Output
- The input provided
- A plot of the information in the source dataset.
    - Hours in X-axis (hours)
    - Drug concentration in Y-axis (mg/L)
- A blue line overlay on the plot to indicate the fit produced using a Linear Model
- A red vertical line overlay on the plot to indicate the hours input by the user
- The prediction from the model as per the model.

---

## Methodology

- A *simplified* version of the `datasets::Theoph` dataset was used to build the model. 
    - The simplification was to collapse two variables: `simTh$GivenDose <- Theoph$Wt * Theoph$Dose`.

- A fit using formula = `lmTh <- lm(conc ~ Time + GivenDose)` was done. Summary of the residuals so obtained are:

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
## -5.7120 -1.4360  0.3952  0.0000  1.8050  5.8150
```

- For sample inputs: `GivenDose=315, Time=4`, prediction for `conc` (using the `predict` function with `interval="prediction",type="response"`) is:


```
##        fit        lwr      upr
## 1 5.197729 -0.2711659 10.66662
```

---

## Other Notes

1. The Shiny app is available at <https://gb-ddp.shinyapps.io/ddp-shiny>.
2. The code for the Shiny app is available at <https://github.com/GopinathanB/ddp-shiny>.
3. The help documentation for the Shiny app is accessible from within the app itself. It can also be accessed at <https://gb-ddp.shinyapps.io/ddp-shiny/ddp-help-documentation.html>.
4. The code for the slidify project (that produced this presentation) is available at <https://github.com/GopinathanB/ddp-shiny>.
