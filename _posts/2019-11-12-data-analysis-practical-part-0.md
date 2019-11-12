---
title: "Data Analysis' Practices - PART 0"
date: 2019-11-12
tags: [data analysis, basics]
categories: [data analysis]
excerpt: "Presenting the basics before starting to create some code"
author_profile: false
mathjax: "true"
---

Before starting anything let's take a look at top programming languages a data scientist should master in 2019 according to [BigData MadeSimple](https://bigdata-madesimple.com/top-8-programming-languages-every-data-scientist-should-master-in-2019/).

##1. Python
Python is an extremely popular general purpose, dynamic, and is a widely used language within the data science community. It is commonly referred to as the easiest programming language to read and to learn. Since it combines quick improvement with the capacity to interface with high-performance algorithms written in Fortran or C, it has become the leading programming language for open data science.
With the advancement of technologies such as artificial intelligence, machine learning, and predictive analytics, the demand for experts with Python skills is rising significantly. It is widely used in web development, scientific computing, data mining, and others.

##2. R
It is one of the most often used tools. R is an open source language and software environment for statistical computing and graphics, supported by the R Foundation for Statistical Computing. This skill sets have high demand across recruiters in machine learning and data science.
R provides many statistical models, and numerous analysts have composed their applications in R.  It is the topper of open statistical analysis, and there is a clear focus on statistical models which have been composed utilizing R. The public R package archive, contains more than 8,000 networks contributed packages. Microsoft, RStudio, and various organizations give business support to R-based computing.

##3. Java
Java is an extremely popular, general purpose language which runs on the Java Virtual Machine (JVM). Many numbers of organizations, particularly MNC organizations use this language to create backend systems and desktop/mobile/web applications. It is an Oracle-supported unique computing system that empowers portability between platforms.
Due to the demand for Java skills is raising, it has been called a pillar of the organization programming stack. Having said that a significant rise in demand, Java skills have been in demand especially for software architects, software engineers, and DevOps engineers.

##4. SQL
SQL (Structured Query Language) is one of the most popular amongst the data science field. It is used well for querying and editing the information stored in a relational database. And also, mainly used for storing and retrieving data for decades. It is used in managing particularly large databases, reducing the turnaround time for online requests by its fast processing time. Having SQL skill can be the biggest asset for machine learning and data science professionals, as SQL is the most preferred skill set for all the organizations.

##5. Julia
Julia is a high-level dynamic programming language designed to address the needs of high-performance numerical analysis, and scientific computing is rapidly gaining popularity amongst the data scientists. It is a newer language, also capable of general purpose programming as well and hasn’t been around as long as R or Python.
Due to its faster execution, Julia has become a perfect choice for dealing with complex projects containing high volume data sets. For many basic benchmarks run 30 times quicker than Python and regularly run somewhat quicker than C code. If you like Python’s syntax while you have a massive amount of data, then Julia is the next programming language to learn.
A joint effort between Jupyter and Julia communities, it gives a fantastic program based graphical notebook interface to Julia. People, who are searching for the best performance parallel computing language focused on numerical computing, Julia is a perfect language for them.

##6. Scala
Scala (scalable language) is one of the best-known languages with one of the largest user bases. It is a general-purpose, open source programming language which runs on the JVM. Scala is an ideal choice of language for those working with high-volume data sets and has full support for functional programming and a strong static type system.
Since it was developed to run on the JVM, it allows interoperability with the Java itself, making Scala a very great general purpose language, while also being a perfect option for data science.
Cluster computing framework Apache Spark is written in Scala. If you want to juggle your data in a thousand processor cluster and have a pile of legacy Java code, then Scala is an incredible open source solution.

##7. MATLAB
It is developed and licensed by MathWorks. It is a quick, stable and ensures solid algorithms for numerical computing language used entire academia and industry. Considered to be a well-suited language for mathematicians and scientists dealing with sophisticated mathematical needs such as Fourier transforms, signal processing, image processing, and matrix algebra.
MATLAB widely used in statistical analysis such as applications or day-to-day role requires intensive, advanced functionality in mathematical makes it a serious option for data science.

8. TensorFlow
TensorFlow is an excellent open source software library for numerical computation. It is a machine learning framework suitable for large-scale data. It works on the basic concept. For instance, if you want to perform a graph of computations in Python, once you defined, then TensorFlow will run it by utilizing a set of tuned C++ code.
One of the most significant advantages of TensorFlow is that the graph can be broken into many chunks that can keep running in parallel over various GPUs or CPUs. And also supports distributed computing; thus, you will be able to train huge neural networks on immense training sets in a short time.
TensorFlow is the second generation system from Google Brain.  It powers a large number of Google’s large-scale services, like Google Search, Google Photos and Google Cloud Speech.

## Conclusion
The landscape of data science is evolving quickly, tools used for extracting value from data science have also increased in numbers. Learning any one of above-mentioned programming languages will kick off your data science career. Though, there is no specific order to this list of popular languages for data science, Python and R fighting for the top spot. However, having more than one language skills give you the versatility and competence as a data scientist.

As you can see it's almost mandatory for data scientists to know all these programming languages, BUT, we are here to learn at least the basics. We'll start slowly, studying some R scripts to analyse .csv datasets.
See you on the next post.


Example of a R code block:
```r
library(tidyverse)
df <- read_csv("some_file.csv")
head(df)
```
