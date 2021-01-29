# SLR- Final Code
Summary of Simple Linear Regression in R
#Load packages
library(ggplot2)
library(dplyr)
library(broom)
library(ggpubr)
#Import data , view and attach data
income.data<-read.csv(file.choose(), header=T)
str(income.data)        
attach(income.data)
summary(income.data)
# Selecting multiple columns that are not next to each other, 2 and 6
income.data[c(2,6)])
# Selecting multiple columns next to each other, 3 to 8
summary(income.data[c(3:8)])
#Omitting a column
summary(income.data[c(-1)])
#Omitting several columns
summary(income.data[c(-1, -3)])
# Selecting multiple columns that are not next to each other
 summary(income.data[c(1,5:10)]
#Normality test of dependent variable
hist(happiness)
#Linearity plot(x,y) or plot(y~x)
plot(income,hapiness)   OR plot(hapiness~income)
Superimpose the regression line, abline(lm(y~x), col=”  “)
abline(lm(happiness~income),col="red")
#Perform LR,  model<-lm(y~x) and view output
model<-lm(happiness~income)
summary(model)

#Make predictions of y - using one and multiple values of x
predict(model, list(income=5))
predict(model,data.frame(income=c(3,4,5)))

#Make predictions of y - using one and multiple values of x with confidence interval
predict(model,data.frame(income=5 ),interval="confidence",level=0.95)
predict(model,data.frame(income=c(3,4,5)),interval="confidence",level=0.95)

#Make predictions of y - using one and multiple values of x with prediction interval
predict(model,data.frame(income=5 ),interval="prediction",level=0.95)
predict(model,data.frame(income=c(3,4,5)),interval="prediction",level=0.95)
#Check for homoscedaciticy
par(mfrow=c(2,2))
plot(model)
USING GGPLOT
#Plot graph
income.graph<-ggplot(incomedata,aes(x=income,y=happiness))+
  geom_point()
income.graph
#Reset plot area incase of error
dev.off()

#Add LR Line 
income.graph <- income.graph + geom_smooth(method="lm", col="black")
income.graph

#Add regression line equation
income.graph <- income.graph + stat_regline_equation(label.x=3, label.y=7)
income.graph

#Add style parameters
income.graph + theme_bw() +
 labs(title="Reported happiness as a function of income",
       x="Income (x$10,000)",
       y = "Happiness score (0 to 10)")

