# Bribery-Oil-and-the-Foreign-Corrupt-Practices-Act
Legal Analytics Final Project
setwd("Desktop/LA Final/")

library(foreign)
install.packages("dplyr")
install.packages("ggplot2")
library(dplyr)
library(ggplot2)


mydata1 <- read.csv("BP Oil.csv", header=T)
mydata2 <- read.csv("CPI Index.csv", header=T)
mydata3 <- read.csv("FCPA.csv", header=T)
mydata4 <- read.csv("Bribe.csv", header=T)


part <- full_join(mydata4,mydata1, by="Country")
final <- full_join(part, mydata3, by="Country")
summary(final)

tbl_df(final)

glimpse(final)

View(final)

final2 <- na.omit(final)

View(final2)

install.packages("tableplot")

library(tableplot)

x <- (final2$Average.Oil)
y <- (final2$Rank)

plot(x,y, main="Oil Reserve v. BPI Rank", xlab="Oil Reserve in Thousand Million Barrels", ylab="Bribe Payers Index Rank", xlim=c(0,300), ylim=c(0,30))


install.packages("calibrate")
library(calibrate)

text(final2$Average.Oil, final2$Rank,labels=final2$Country, cex=0.5, pos=4, col="blue")

text(final2$Average.Oil, final2$Rank,labels=final2$Enforcement.Actions, cex=0.5, pos=2, col="red")

grid(nx = NULL, ny = NULL, col = "lightgray", lty = "dotted")
