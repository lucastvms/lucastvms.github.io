---
title: "Introduction to Data Analysis"
date: 2019-10-24
tags: [data analysis, introduction, data mining]
categories: [data analysis]
excerpt: "Talking about what is data analysis, its principles and how it's done"
author_profile: false
mathjax: "true"
---
## What is Data Analysis?
The process of inspecting, cleaning, transforming, and modeling data with the objective of discovering useful information, arriving at conclusions, and supporting the decision making process is called **Data Analysis**.

## Data Analysis and its varieties.
There are multiple facets and approaches with diverse techniques for data analysis. The data analysis in statistics are generally divided into descriptive statistics, exploratory data analisys (EDA), and confirmatory data analysis (CDA). Data need to be cleaned. Data cleaning is the process of correcting the outliers and other incorrect and unwanted information. There are several types of data cleaning proecss to employ depends on the tpe of data to be cleaned. For quantitative data methods the outlier detection can be used to get rid of anomaly in the data. Spellcheckers can be used to lessen the amount of mysteped words in case of textual data.

Business intelligence covers the data analysis that run heavely on aggregation, disaggregation, slicing and dicing, fosusing on the business information. Predictive analytics is the application of statistical or structural models for predictive forecasting. Text analytics is the application of statistical, linguistic, and structural models to extract and classify information from texts.

*Steps of Data Analysis (Next Post):*
![alt]({{ site.url }}{{ site.baseurl }}/assets/images/data-analysis/steps.png)

R code block:
```r
library(dplyr)
library(ggplot2)
library(tidyr)

path <- "{{ site.url }}{{ site.baseurl }}/assets/"

hsb2 = read.csv(paste(path,"hsb2.csv",sep=""))

str(hsb2)

glimpse(hsb2)

table(hsb2$schtyp)

hsb2_public <- filter(hsb2, schtyp == "public")

str(hsb2)

str(hsb2_public)


table(hsb2_public$schtyp)

str(hsb2_public$schtyp)

hsb2_public$schtyp <- droplevels(hsb2_public$schtyp)

str(hsb2_public$schtyp)

str(hsb2)

hsb2_private <- hsb2 %>% filter(schtyp == "private")

ggplot(data = hsb2, aes(x = science, y = math, color = prog)) + geom_point()

county = read.csv(paste(path,"countyComplete.csv",sep=""))

str(county)
county_noDC <- county %>% filter(state != "District of Columbia") %>% droplevels()

county_srs <- county_noDC %>% sample_n(size = 150)

glimpse(county_srs)

comics = read.csv(paste(path,"comics.csv",sep=""))
comics

levels(comics$align)

ggplot(comics, aes(x = id, fill = align)) + geom_bar()

options(scipen = 999, digits = 3)

tab_cnt <- table(comics$id, comics$align)
tab_cnt

prop.table(tab_cnt)

prop.table(tab_cnt,1)

prop.table(tab_cnt,2)

ggplot(comics, aes(x = id, fill = align)) + geom_bar(position = "fill") + ylab("proportion")

cars <- read.csv(paste(path,"cars.csv",sep=""))
str(cars)

life <- read.csv(paste(path,"life.csv",sep=""))
str(life)
x <- head(life$Male.life.expectancy..years., 11)  
mean(x)
table(x)

wide_df <- data.frame(c("x", "y"), c(1,4), c(2,5), c(3,6))

colnames(wide_df) <- c("col", "A", "B","C")

wide_df

long_df <- gather(wide_df, my_key, my_val, -col)

long_df

spread(long_df, my_key, my_val)


inf_df <- data.frame(Name = c("jake", "Alice", "Tim", "Denise"),
                     age = c(34, 55, 76, 19),
                     brown = c(0,0,1,0),
                     blue = c(0,1,0,0),
                     other = c(1,0,0,1),
                     height = c(61,59,57,51))
gather(inf_df, color, value, -c(Name, age, height))


treatments <- data.frame(patient = c("X", "Y", "X", "Y","X","Y"),
                     treatment = c("A", "A", "B", "B","C","C"),
                     year_mo = c("2010-10","2010-10","2012-08","2012-08","2014-12", "2014-12"),
                     response = c(1, 4, 2, 5, 3 ,6))

separate(treatments, year_mo, c("year", "month"))

```
