###Introduction
This first quiz will check your ability to execute basic operations on objects in R and to
understand some basic concepts. For questions 11-20 you will need to load a dataset into R
and do some basic manipulations in order to answer the questions on the quiz.
You may want to print a copy of the quiz questions to look at as you work on the assignment. It
is recommended that you save your answers as you go in the event that a technical problem
should occur with your network connection or computer. Ultimately, you must submit the quiz
online to get credit!

###Data
The zip file containing the data for questions 11-20 in this Quiz can be downloaded here:
[Week 1 Quiz Data](https://d396qusza40orc.cloudfront.net)
For this assignment you will need to unzip this file in your working directory.

**Question 1**
============
R was developed by statisticians working at

a)The University of Auckland

**Question 2**
============
The definition of free software consists of four freedoms (freedoms 0 through 3). Which of the
following is NOT one of the freedoms that are part of the definition?

c)The freedom to sell the software for any price.

**Question 3**
============
In R the following are all atomic data types EXCEPT:

a)matrix

**Question 4**
============
If I execute the expression x <- 4 in R, what is the class of the object `x' as determined by the
`class()' function?

c)numeric

**Question 5**
============
What is the class of the object defined by the expression x <- c(4, "a", TRUE)?

c)character

**Question 6**
============
If I have two vectors x <- c(1,3, 5) and y <- c(3, 2, 10), what is produced by the expression
cbind(x, y)?

c)a 3 by 2 numeric matrix

**Question 7**
============
A key property of vectors in R is that:

d)elements of a vector all must be of the same class

**Question 8**
============
Suppose I have a list defined as x <- list(2, "a", "b", TRUE). What does x[[1]] give me?

a)a list containing the letter "a".

**Question 9**
============
Suppose I have a vector x <- 1:4 and a vector y <- 2.
What is produced by the expression x + y?

c)a numeric vector with elements 3, 4, 5, 6.

**Question 10**
=============
Suppose I have a vector x <- c(3, 5, 1, 10, 12, 6) and I want to set all elements of this vector that
are less than 6 to be equal to zero. What R code achieves this?

d)x[x < 6] <- 0

**Question 11**
=============
In the dataset provided for this Quiz, what are the column names of the dataset?

b)Ozone, Solar.R, Wind,Temp, Month, Day


```r
zipFile <- "rprog-data-quiz1_data.zip"
csvFile <- "hw1_data.csv"
initial <- read.csv(unz(zipFile, csvFile), nrows = 10 )
colClasses <- sapply(initial,class)
data <- read.csv(unz(zipFile, csvFile), header = T, sep = ",",
                 na.strings = "NA", colClasses = colClasses)
theNames <- names(data)
```

***answer*** : Ozone, Solar.R, Wind, Temp, Month, Day 

**Question 12**
=============
Extract the first 2 rows of the data frame and print them to the console. What does the output
look like?


```r
first2Rows <- data[1:2, ] 
first2Rows ## answer
```

```
##   Ozone Solar.R Wind Temp Month Day
## 1    41     190  7.4   67     5   1
## 2    36     118  8.0   72     5   2
```
 

**Question 13**
=============
How many observations (i.e. rows) are in this data frame?


```r
obs <- nrow(data)
```

***answer*** : 153

**Question 14**
=============
Extract the last 2 rows of the data frame and print them to the console. What does the output
look like?

```r
last2Rows <- data[152:153, ]
last2Rows # answer
```

```
##     Ozone Solar.R Wind Temp Month Day
## 152    18     131  8.0   76     9  29
## 153    20     223 11.5   68     9  30
```


**Question 15**
=============
What is the value of Ozone in the 47th row?


```r
ozon47 <- data[47,"Ozone"]
```

***answer*** : 21

**Question 16**
=============
How many missing values are in the Ozone column of this data frame?


```r
bad <- sum(is.na(data[,"Ozone"]))
```

***answer*** : 37

**Question 17**
=============
What is the mean of the Ozone column in this dataset? Exclude missing values (coded as NA)


```r
meanvalueOzon1 <- mean(data$Ozone, na.rm = T)
meanValueOzon2 <- mean(data[,"Ozone"], na.rm = T)
```

***answer*** : `meanValueOzon1`

**Question 18**
=============
Extract the subset of rows of the data frame where Ozone values are above 31 and Temp values
are above 90. What is the mean of Solar.R in this subset?


```r
extract1 <- data[data$Ozone > 31 & data$Temp > 90, ]
meanValue <- mean(extract1$Solar.R, na.rm = T )
```

***answer*** : 212.8

**Question 19**
=============
What is the mean of "Temp" when "Month" is equal to 6?


```r
extract2 <- data[data$Month == 6, ]
meanTemp <- mean(extract2$Temp, na.rm = T)
```
***answer***: 79.1

**Question 20**
=============
What was the maximum ozone value in the month of May (i.e. Month = 5)?


```r
good <- complete.cases(data)
extract3 <- data[good,][data$Month == 5,]
maxOzon <- max(extract3$Ozone)
```

***answer*** : 115
