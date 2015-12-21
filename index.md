---
title       : Respiratory Cancer Query Tool
subtitle    : Design Document
author      : Geethanjali Arun
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## What does this application do?


1. This application is a data exploration and visualization tool for the respiratory cancer counts and rates across the United states.
2. Data is sourced from the CDC website.
3. Data covers all the regions.
4. Data covers the time period 1999 - 2012.
5. Data has 5 variables : cancer site, age group, gender, race and ethnicity.
6. The count metric reports the frequency of verified cancer diagnoses in the selected population.
7. The crude rate is expressed as the number of cases reported each calendar year per 100,000 population.

--- .class #id 

## Summarise page

1. This page displays the count and crude rate for the selected inputs.

2. The page has 5 drop down menus.

3. The inputs are the desired cancer site, age group, gender, race and ethnicity.

4. The drop down shows the available options.

5. A click on the 'GET' button displays the metrics on the right side panel, instantaneously.

--- 

## Visualize page

1. This page displays the count in a bar chart format.

2. It has an input field with a drop down menu showing 5 options.

3. Once the 'PLOT' button is pressed, the bar chart is displayed on the right panel.

4. The plot shows the count, with the legend. 

---

## Sample Query



```r
colClassVector = c("character", "factor", "factor", "factor", "factor",
                   "factor","factor","factor", "factor", "factor", 
                   "factor", "numeric", "numeric", "numeric")
cancerData = read.delim("resp_cancer_data.txt",header = TRUE,
                        sep="\t", na.strings = "Not Applicable",
                        nrows = 839)
d = group_by(cancerData, Cancer.Sites) 
m = filter(d, Cancer.Sites == "Larynx" & Age.Group.Code == "20-24" 
           & Sex.Code == "M" & Race == "White" & Ethnicity == "Non-Hispanic")
```

```
## [1] "Count and Crude Rate for Larnyx,20-24,Male,White,Non-Hispanic is "
```

```
## [1] 28
```

```
## [1] 0.03
```

