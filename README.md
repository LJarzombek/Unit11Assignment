# Unit11Assignment
Assigment is for Section 6306, Unit 404 
Southern Methodist University
In Class Assignment Unit #11
---
title: "Live Session Unit 11 Assignment"
author: "Laura Jarzombek"
date: "November 18, 2016"
output: html_document
---
  
  ## R Markdown
  ###1)	Go through the electric equipment example. Answer the following questions using "Visitors"" Dataset:


####Load Library called "fpp". 
```{r}

library(fpp) #fpp package must be installed first

```


####a)	Plot the time series. Can you identify seasonal fluctuations and/or a trend? 
```{r}
data("visitors")

```

```{r visitors, echo=FALSE}
plot(visitors)

#### The number of visitors is trending upward (increasing) over time. Per the above plot, it also appears that there is some cyclicality and fluctuation on an annual basis, with a noticeable spike in visitors on a per year basis.  
```

####b)	Use a classical decomposition to calculate the trend-cycle and seasonal indices.
```{r}
fitd<-decompose(visitors)
####Decomposed data set. 
```

####c)	Do the results support the graphical interpretation from part (a)? 
```{r fitd, echo=FALSE}
plot(fitd)
####Yes, the results support the graphical interpretation from part (a).
```


####d)	Compute and plot the seasonally adjusted data. 
```{r}
eeadj<-seasadj(fitd)
```
####Data adjusted for seasonality. 

####Plot for seasonally adjusted data in (d)
```{r eedj, echo=FALSE}
plot(eeadj)
####Data plotted after adjusting for seasonality. 
```


####e)	Change one observation to be an outlier (e.g., add 500 to one observation), and recompute the seasonally adjusted data. What is the effect of the outlier? 
```{r}
eeadj[3]=675.4
#### Changed one observation to be an outlier. Recomputed seasonally adjusted data. The effect of the outlier is a spike early on in the plot.
```


####f)	Does it make any difference if the outlier is near the end rather than in the middle of the time series? 
```{r, echo=FALSE}
plot(eeadj)

####No, it does not make a difference if the outlier is near the end rather than the middle of the time series. 

```


####g)	Use STL to decompose the series. 
```{r}
fit<-stl(visitors, s.window=5)

####Used STL to decompose the series.

```

####Plot series.
```{r fit, echo=FALSE}
plot(fit)
####Plotted series. 
