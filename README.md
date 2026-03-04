
<!-- README.md is generated from README.Rmd. Please edit the README.Rmd file -->

# Lab report \#1

Follow the instructions posted at
<https://ds202-at-isu.github.io/labs.html> for the lab assignment. The
work is meant to be finished during the lab time, but you have time
until Monday evening to polish things.

Include your answers in this document (Rmd file). Make sure that it
knits properly (into the md file). Upload both the Rmd and the md file
to your repository.

All submissions to the github repo will be automatically uploaded for
grading once the due date is passed. Submit a link to your repository on
Canvas (only one submission per team) to signal to the instructors that
you are done with your submission.

## Step 1 Result

``` r
library(classdata)
str(ames)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    6935 obs. of  16 variables:
    ##  $ Parcel ID            : chr  "0903202160" "0907428215" "0909428070" "0923203160" ...
    ##  $ Address              : chr  "1024 RIDGEWOOD AVE, AMES" "4503 TWAIN CIR UNIT 105, AMES" "2030 MCCARTHY RD, AMES" "3404 EMERALD DR, AMES" ...
    ##  $ Style                : Factor w/ 12 levels "1 1/2 Story Brick",..: 2 5 5 5 NA 9 5 5 5 5 ...
    ##  $ Occupancy            : Factor w/ 5 levels "Condominium",..: 2 1 2 3 NA 2 2 1 2 2 ...
    ##  $ Sale Date            : Date, format: "2022-08-12" "2022-08-04" ...
    ##  $ Sale Price           : num  181900 127100 0 245000 449664 ...
    ##  $ Multi Sale           : chr  NA NA NA NA ...
    ##  $ YearBuilt            : num  1940 2006 1951 1997 NA ...
    ##  $ Acres                : num  0.109 0.027 0.321 0.103 0.287 0.494 0.172 0.023 0.285 0.172 ...
    ##  $ TotalLivingArea (sf) : num  1030 771 1456 1289 NA ...
    ##  $ Bedrooms             : num  2 1 3 4 NA 4 5 1 3 4 ...
    ##  $ FinishedBsmtArea (sf): num  NA NA 1261 890 NA ...
    ##  $ LotArea(sf)          : num  4740 1181 14000 4500 12493 ...
    ##  $ AC                   : chr  "Yes" "Yes" "Yes" "Yes" ...
    ##  $ FirePlace            : chr  "Yes" "No" "No" "No" ...
    ##  $ Neighborhood         : Factor w/ 42 levels "(0) None","(13) Apts: Campus",..: 15 40 19 18 6 24 14 40 13 23 ...

``` r
#?ames
```

Variables in ames dataset:

Parcel ID: character with ID (int) Address: property address (str)
Style: factor variable in type of housing (str) Occupancy: factor
variable in type of housing (str) Sale Date: date of sale (date) Sale
Price: sales price (int) Multi Sale: was this sale part of a package?
(bool) YearBuilt: year in which house was built (int) Acres: acres of
the lot (double) TotalLivingArea (sf): total living area in square feet
(int) Bedrooms: num of bedrooms (int) FinishedBsmtArea (sf): total area
of finished basement (int) LotArea (sf): total lot area (int) AC: does
the property have AC? (bool) FirePlace: does the property have a
fireplace? (bool) Neighborhood: factor variable to indicate neighborhood
(str)

## Step 2 Result

Main variable: Sale Price. We will focus on this variable.

## Step 3 Result

``` r
data(ames)
range(ames$`Sale Price`)
```

    ## [1]        0 20500000

``` r
library(ggplot2)
ggplot(ames, aes(x = `Sale Price`)) +
  geom_histogram(binwidth = 100000, position="stack")
```

![](README_files/figure-gfm/range-1.png)<!-- -->

The histogram shows that most of the data is concentrated on the left
side of the graph, with some outliers on the right side. This shows that
the distribution of Sale Price is not uniform.

## Step 4 Result

### Chaitanya’s Work:

``` r
# range
range(ames$`TotalLivingArea (sf)`, na.rm = TRUE)
```

    ## [1]    0 6007

``` r
# histogram
hist(ames$`TotalLivingArea (sf)`,
     main = "Distribution of Total Living Area",
     xlab = "Total Living Area (sq ft)",
     col = "lightblue")
```

![](README_files/figure-gfm/TotalLivingArea-1.png)<!-- -->

``` r
# scatterplot with Sale Price
plot(ames$`TotalLivingArea (sf)`, ames$`Sale Price`,
     main = "Sale Price vs Total Living Area",
     xlab = "Total Living Area (sq ft)",
     ylab = "Sale Price",
     pch = 19,
     col = "pink")
```

![](README_files/figure-gfm/TotalLivingArea-2.png)<!-- --> Summary: The
variable TotalLivingArea (sf) represents the total living space of a
house in square feet. The values range from about 0 to around 6000
square feet. The histogram shows that most houses have living areas
between 1000 and 2000 square feet, with fewer houses having very large
living areas. The distribution is slightly right-skewed because a small
number of houses have much larger living areas.

The scatterplot comparing TotalLivingArea and Sale Price does not show a
clear positive trend because many houses have a Sale Price of 0, which
creates a horizontal cluster of points near the bottom of the plot.
These values are likely missing or incorrect data entries, which makes
the relationship harder to see. If those values were removed, we would
expect larger houses to generally have higher sale prices.

### Kalyna’s Work:

### Mariana’s Work:

### Sebastian’s Work:

I choose to work with the variable ‘LotArea(sf)’.

``` r
data(ames)
range(ames$`LotArea(sf)`)
```

    ## [1] NA NA

``` r
library(ggplot2)
ggplot(data = ames, aes(x = `Sale Price`, y = `LotArea(sf)`)) +
  geom_point() +
  labs(title = "Scatter Plot of Sale Price vs. LotArea(sf)",
       x = "Sale Price",
       y = "Lot Area (in square feet")
```

    ## Warning: Removed 89 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->
