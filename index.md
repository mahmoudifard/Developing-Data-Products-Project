---
title       :   Developing Data Products Project
subtitle    :   Calculating total calleries someone needed
author      :   Seyed Mahmoudifard
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Read the data
**Three elements are very important in determining the total calleries that body needs**  
1. Weight  
2. Height  
3. Age  
using these R codes, the data collected.

```r
       numericInput('weight', 'Weight (lb)',150, min = 70, max = 400, step = 1),
       numericInput('height', 'Height (inches)',70, min = 30, max = 100, step = 1),
       numericInput('age', 'Age',25, min = 1, max = 130, step = 1)
```

--- .class #id 

## calculation

**the formula that was used for callery colculation is as below:**  

```r
66.7+ (13.75*weight) + (5.0*height) - (6.75*age)
```


--- .class #id  

## server codes  

**server codes are as below**  

```r
library(shiny)
shinyServer(function(input, output) {
      calleriesneeded<- reactive({66.7+ (13.75*input$weight) + (5.0*input$height) - (6.75*input$age)})
      output$calleries<- calleriesneeded
})
```

--- .class #id 

## Example
**for example, for a person with 65 inches height, 125 lb weight, and 25 years old, the daily calleries shouls be 1941 calleries**  

