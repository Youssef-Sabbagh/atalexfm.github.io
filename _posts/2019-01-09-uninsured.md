---
title: "Uninsured Americans and Poverty"
date: 2019-01-09
tags: [data science, statistical analysis, linear regression]
header:
    image: "/images/lights.JPG"
excerpt: "Data Science, Poverty, Uninsured Rates" 
---

# Uninsured Americans and Poverty 

## Executive Overview

This report explores the relationship between health insurance and poverty in the United States, and particularly, if there is a relationship between being economially disadvantaged and being uninsured. I found that there is a significant relationship between uninsured rates and unemployment rates, per capita income, and number of households impoverished; however, there is little relationship between uninsured rates and poverty rates. 

## Problem Statement

I investigated the relationship between poverty and health insurance, particularly, is poverty associated with a lack of insurance. Though the United States offers impoverished Americans health insurance through Medicaid and offers affordable healthcare through the Affordable Care Act, yet, as of 2016, approximately 27.3 million Americans remain uninsured (U.S. Census). In a survey of uninsured Americans conducted in 2017, 45 percent said that they are uninsured because the cost of being insured is too high (KFF). This problem is critical because as of 2009, approximately 45,000 deaths annually are associated with lack of insurance. Furthermore, uninsured, working age Americans have a 40 percent higher risk of death than insured Americans of the same age range (Harvard). Knowing the underlying evidences of the problem, I investigated independent variables related to poverty. I collected and processed data pertaining to uninsured rates, the dependent variable, and unemployment rates, per capita household income, number of households impoverished, and poverty rates, the independent variables. I used unemployment rates, per capita household income, number of households impoverished, and poverty rates because they are both generalized and specified indicators of poverty, and shifts in these indicators may attribute to changes in uninsured rates.

## Results

The regression outcome indicates that there is a significant relationship between uninsured rates and per capita income, unemployment rates, and number of impoverished households and little relationship between uninsured rates and poverty rates. The p-value of the regression is .00009339, meaning that the null hypothesis, uninsured rates is not related to poverty, is not rejected. As seen in Table 1.1, the p-values of impoverished households, unemployment rates, and per capita income is 0.035188, 0.007984, and 0.001314 respectively. The p-values of these independent variables indicate that there is a correlation to the dependent variable, uninsured rates. The p-values of the three independent variables are significant and further support the underlying evidences presented in the problem statement above. In regard to unemployment rates, in 2013 70.8 percent of all workers between the ages of 18 and 64 received health insurance through their employers (CNBC). In short, if a worker is unemployed, they are less likely to have health insurance, therefore, suggesting the possibility of a relationship. Further, there is evidence to support a relationship between uninsured rates and per capita income and impoverished households. In 2016, 27.3 million people did not have health insurance, and of those 27.3 million, 28.6 percent did not graduate high school, and people with less education tend to be in a lower socio-economic bracket (U.S. Census). 

<img src="{{ site.url }}{{ site.baseurl }}/images/uninsured/intercept.png" alt="coefficients">

* Table 1.1: Coefficients of the regression

In the scope of the model as it directly pertains to the data, I examined the adjusted R-square, and constructed a residuals vs fitted plot. The adjusted R-squared is .3494, which states that 34.94 percent of the variation in the dependent variable, uninsured rates, is explained by the four independent variables. Upon further examination of the data, the residual vs fitted plot illustrates that the data are randomly distributed along the horizontal axis. This suggests that the data are a good fit for the linear model.


<img src="{{ site.url }}{{ site.baseurl }}/images/uninsured/residual_fitted.png" alt="residual plot">

* Graph 1.1: Plot of residual values vs. fitted values

This project investigated the relationship between poverty and health insurance and after conducting this experiment, it clarified the relationship; there is a significant relationship between impoverished Americans and their insured status.

### Linear Regression in R

``` 
# Reads the hc_uninsured_dataset and runs a multiple linear regression

# Attaches hc_uninsured_datset 
attach(hc_uninsured_dataset_xlsx)

# Display column names 
names(hc_uninsured_dataset_xlsx)

# Display the data
hc_uninsured_dataset_xlsx

# Assign the independent variable 
uninsured <- c(hc_uninsured_rate)

# Assign the dependent variables
pov_house <- c(pov_house_income_thousands)
pov_rate <- c(pov_rate)
unemployment <- c(unemployment_rate)
income <-c(income_per_capita)

# Runs a multiple linear regression
uninsured_regression <- lm(uninsured ~ pov_house + pov_rate 
                           + unemployment + income)

# Displays results of multiple linear regression
summary(uninsured_regression)

# Displays confidence interval
confint(uninsured_regression, level = 0.95)
plot(uninsured_regression)
```