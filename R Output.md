# Bribery-Oil-and-the-Foreign-Corrupt-Practices-Act
Legal Analytics Final Project
> setwd("Desktop/LA Final/")
> library(foreign)
> install.packages("dplyr")
trying URL 'http://cran.rstudio.com/bin/macosx/mavericks/contrib/3.2/dplyr_0.4.1.tgz'
Content type 'application/x-gzip' length 4884470 bytes (4.7 MB)
==================================================
downloaded 4.7 MB


The downloaded binary packages are in
	/var/folders/bk/1xrrcvwn05x07dlyb99vdkpc0000gn/T//RtmpCLuFvl/downloaded_packages
> install.packages("ggplot2")
trying URL 'http://cran.rstudio.com/bin/macosx/mavericks/contrib/3.2/ggplot2_1.0.1.tgz'
Content type 'application/x-gzip' length 2670945 bytes (2.5 MB)
==================================================
downloaded 2.5 MB


The downloaded binary packages are in
	/var/folders/bk/1xrrcvwn05x07dlyb99vdkpc0000gn/T//RtmpCLuFvl/downloaded_packages
> library(dplyr)

Attaching package: ‘dplyr’

The following object is masked from ‘package:stats’:

    filter

The following objects are masked from ‘package:base’:

    intersect, setdiff, setequal, union

> library(ggplot2)
Need help? Try the ggplot2 mailing list: http://groups.google.com/group/ggplot2.
> mydata1 <- read.csv("BP Oil.csv", header=T)
> mydata2 <- read.csv("CPI Index.csv", header=T)
> mydata3 <- read.csv("FCPA.csv", header=T)
> mydata4 <- read.csv("Bribe.csv", header=T)
> part <- full_join(mydata4,mydata1, by="Country")
Warning message:
In outer_join_impl(x, y, by$x, by$y) :
  joining factors with different levels, coercing to character vector
> final <- full_join(part, mydata3, by="Country")
Warning message:
In outer_join_impl(x, y, by$x, by$y) :
  joining factor and character vector, coercing into character vector
> summary(final)
   Country               Rank          Oil.1995         Oil.1996         Oil.1997     
 Length:83          Min.   : 1.00   Min.   :  0.00   Min.   :  0.00   Min.   :  0.00  
 Class :character   1st Qu.: 7.50   1st Qu.:  0.76   1st Qu.:  0.76   1st Qu.:  0.76  
 Mode  :character   Median :14.50   Median :  3.13   Median :  3.45   Median :  3.67  
                    Mean   :13.96   Mean   : 20.41   Mean   : 20.86   Mean   : 21.15  
                    3rd Qu.:19.75   3rd Qu.: 10.80   3rd Qu.: 11.68   3rd Qu.: 12.50  
                    Max.   :28.00   Max.   :261.45   Max.   :261.44   Max.   :261.54  
                    NA's   :55      NA's   :34       NA's   :34       NA's   :34      
    Oil.1998         Oil.1999         Oil.2000         Oil.2001         Oil.2002     
 Min.   :  0.00   Min.   :  0.00   Min.   :  0.00   Min.   :  0.00   Min.   :  0.00  
 1st Qu.:  1.02   1st Qu.:  1.18   1st Qu.:  1.17   1st Qu.:  1.16   1st Qu.:  1.13  
 Median :  4.10   Median :  4.74   Median :  4.57   Median :  4.54   Median :  4.57  
 Mean   : 22.19   Mean   : 25.14   Mean   : 25.56   Mean   : 25.74   Mean   : 26.85  
 3rd Qu.: 17.42   3rd Qu.: 15.11   3rd Qu.: 16.87   3rd Qu.: 16.84   3rd Qu.: 17.20  
 Max.   :261.54   Max.   :262.78   Max.   :262.77   Max.   :262.70   Max.   :262.79  
 NA's   :34       NA's   :34       NA's   :34       NA's   :34       NA's   :34      
    Oil.2003         Oil.2004         Oil.2005         Oil.2006         Oil.2007     
 Min.   :  0.00   Min.   :  0.00   Min.   :  0.00   Min.   :  0.00   Min.   :  0.00  
 1st Qu.:  1.28   1st Qu.:  1.33   1st Qu.:  1.45   1st Qu.:  1.51   1st Qu.:  1.51  
 Median :  4.73   Median :  4.30   Median :  4.19   Median :  4.46   Median :  4.07  
 Mean   : 27.11   Mean   : 27.30   Mean   : 27.50   Mean   : 27.73   Mean   : 28.46  
 3rd Qu.: 16.04   3rd Qu.: 15.53   3rd Qu.: 15.59   3rd Qu.: 15.61   3rd Qu.: 27.32  
 Max.   :262.73   Max.   :264.31   Max.   :264.21   Max.   :264.25   Max.   :264.21  
 NA's   :34       NA's   :34       NA's   :34       NA's   :34       NA's   :34      
    Oil.2008         Oil.2009         Oil.2010         Oil.2011         Oil.2012     
 Min.   :  0.00   Min.   :  0.00   Min.   :  0.00   Min.   :  0.00   Min.   :  0.43  
 1st Qu.:  1.50   1st Qu.:  1.50   1st Qu.:  1.60   1st Qu.:  1.60   1st Qu.:  1.60  
 Median :  5.00   Median :  4.50   Median :  4.50   Median :  4.40   Median :  4.20  
 Mean   : 29.93   Mean   : 30.78   Mean   : 32.96   Mean   : 33.78   Mean   : 34.28  
 3rd Qu.: 26.83   3rd Qu.: 25.91   3rd Qu.: 24.68   3rd Qu.: 23.90   3rd Qu.: 25.23  
 Max.   :264.06   Max.   :264.59   Max.   :296.50   Max.   :297.57   Max.   :297.57  
 NA's   :34       NA's   :34       NA's   :34       NA's   :34       NA's   :34      
    Oil.2013       Average.Oil     Enforcement.Actions
 Min.   :  0.43   Min.   :  0.37   Min.   : 1.000     
 1st Qu.:  1.60   1st Qu.:  1.28   1st Qu.: 1.000     
 Median :  3.96   Median :  4.47   Median : 1.500     
 Mean   : 34.29   Mean   : 27.47   Mean   : 3.182     
 3rd Qu.: 25.06   3rd Qu.: 20.17   3rd Qu.: 3.000     
 Max.   :298.35   Max.   :263.53   Max.   :39.000     
 NA's   :34       NA's   :34       NA's   :39         
> tbl_df(final)
Source: local data frame [83 x 23]

       Country Rank Oil.1995 Oil.1996 Oil.1997 Oil.1998 Oil.1999 Oil.2000 Oil.2001
1  Netherlands    1       NA       NA       NA       NA       NA       NA       NA
2  Switzerland    1       NA       NA       NA       NA       NA       NA       NA
3      Belgium    3       NA       NA       NA       NA       NA       NA       NA
4      Germany    4       NA       NA       NA       NA       NA       NA       NA
5        Japan    4       NA       NA       NA       NA       NA       NA       NA
6    Australia    6     3.80     3.82     4.04     4.77     4.74     4.94     4.96
7       Canada    6    48.37    48.94    48.80    49.82   181.56   181.50   180.94
8    Singapore    8       NA       NA       NA       NA       NA       NA       NA
9           UK    8       NA       NA       NA       NA       NA       NA       NA
10         USA   10       NA       NA       NA       NA       NA       NA       NA
..         ...  ...      ...      ...      ...      ...      ...      ...      ...
Variables not shown: Oil.2002 (dbl), Oil.2003 (dbl), Oil.2004 (dbl), Oil.2005 (dbl),
  Oil.2006 (dbl), Oil.2007 (dbl), Oil.2008 (dbl), Oil.2009 (dbl), Oil.2010 (dbl),
  Oil.2011 (dbl), Oil.2012 (dbl), Oil.2013 (dbl), Average.Oil (dbl), Enforcement.Actions
  (int)
> glimpse(final)
Observations: 83
Variables:
$ Country             (chr) "Netherlands", "Switzerland", "Belgium", "Germany", "Japa...
$ Rank                (int) 1, 1, 3, 4, 4, 6, 6, 8, 8, 10, 11, 11, 13, 14, 15, 15, 15...
$ Oil.1995            (dbl) NA, NA, NA, NA, NA, 3.80, 48.37, NA, NA, NA, NA, NA, NA, ...
$ Oil.1996            (dbl) NA, NA, NA, NA, NA, 3.82, 48.94, NA, NA, NA, NA, NA, NA, ...
$ Oil.1997            (dbl) NA, NA, NA, NA, NA, 4.04, 48.80, NA, NA, NA, NA, NA, NA, ...
$ Oil.1998            (dbl) NA, NA, NA, NA, NA, 4.77, 49.82, NA, NA, NA, NA, NA, NA, ...
$ Oil.1999            (dbl) NA, NA, NA, NA, NA, 4.74, 181.56, NA, NA, NA, NA, NA, NA,...
$ Oil.2000            (dbl) NA, NA, NA, NA, NA, 4.94, 181.50, NA, NA, NA, NA, NA, NA,...
$ Oil.2001            (dbl) NA, NA, NA, NA, NA, 4.96, 180.94, NA, NA, NA, NA, NA, NA,...
$ Oil.2002            (dbl) NA, NA, NA, NA, NA, 4.57, 180.40, NA, NA, NA, NA, NA, NA,...
$ Oil.2003            (dbl) NA, NA, NA, NA, NA, 3.75, 180.37, NA, NA, NA, NA, NA, NA,...
$ Oil.2004            (dbl) NA, NA, NA, NA, NA, 3.89, 180.04, NA, NA, NA, NA, NA, NA,...
$ Oil.2005            (dbl) NA, NA, NA, NA, NA, 3.72, 180.49, NA, NA, NA, NA, NA, NA,...
$ Oil.2006            (dbl) NA, NA, NA, NA, NA, 3.51, 179.81, NA, NA, NA, NA, NA, NA,...
$ Oil.2007            (dbl) NA, NA, NA, NA, NA, 3.43, 178.83, NA, NA, NA, NA, NA, NA,...
$ Oil.2008            (dbl) NA, NA, NA, NA, NA, 4.24, 176.26, NA, NA, NA, NA, NA, NA,...
$ Oil.2009            (dbl) NA, NA, NA, NA, NA, 4.06, 175.87, NA, NA, NA, NA, NA, NA,...
$ Oil.2010            (dbl) NA, NA, NA, NA, NA, 3.83, 175.22, NA, NA, NA, NA, NA, NA,...
$ Oil.2011            (dbl) NA, NA, NA, NA, NA, 3.87, 174.59, NA, NA, NA, NA, NA, NA,...
$ Oil.2012            (dbl) NA, NA, NA, NA, NA, 3.92, 174.32, NA, NA, NA, NA, NA, NA,...
$ Oil.2013            (dbl) NA, NA, NA, NA, NA, 3.96, 174.32, NA, NA, NA, NA, NA, NA,...
$ Average.Oil         (dbl) NA, NA, NA, NA, NA, 4.10, 151.08, NA, NA, NA, NA, NA, NA,...
$ Enforcement.Actions (int) NA, 1, NA, 3, NA, 1, 1, NA, NA, NA, NA, NA, NA, 9, 1, 5, ...
> View(final)
> final2 <- na.omit(final)
> View(final2)
> install.packages("tableplot")
trying URL 'http://cran.rstudio.com/bin/macosx/mavericks/contrib/3.2/tableplot_0.3-5.tgz'
Content type 'application/x-gzip' length 56903 bytes (55 KB)
==================================================
downloaded 55 KB


The downloaded binary packages are in
	/var/folders/bk/1xrrcvwn05x07dlyb99vdkpc0000gn/T//RtmpCLuFvl/downloaded_packages
> library(tableplot)
Loading required package: grid
> x <- (final2$Average.Oil)
> y <- (final2$Rank)
> plot(x,y, main="Oil Reserve v. BPI Rank", xlab="Oil Reserve in Thousand Million Barrels", ylab="Bribe Payers Index Rank", xlim=c(0,300), ylim=c(0,30))
> install.packages("calibrate")
trying URL 'http://cran.rstudio.com/bin/macosx/mavericks/contrib/3.2/calibrate_1.7.2.tgz'
Content type 'application/x-gzip' length 306954 bytes (299 KB)
==================================================
downloaded 299 KB


The downloaded binary packages are in
	/var/folders/bk/1xrrcvwn05x07dlyb99vdkpc0000gn/T//RtmpCLuFvl/downloaded_packages
> library(calibrate)
Loading required package: MASS

Attaching package: ‘MASS’

The following object is masked from ‘package:dplyr’:

    select

> text(final2$Average.Oil, final2$Rank,labels=final2$Country, cex=0.5, pos=4, col="blue")
> text(final2$Average.Oil, final2$Rank,labels=final2$Enforcement.Actions, cex=0.5, pos=2, col="red")
> grid(nx = NULL, ny = NULL, col = "lightgray", lty = "dotted")
