
Data Structures and Subsetting
==============================

In this tutorial we are trying to demonstrate basic operations with data structures and subsetting in R software. This file is part of my project for Statistical Computing with Prof. Harner. \#\#\#\# Explain your code where appropriate.

1.  Create vectors of each of the different primitive types. i.e., integer, double, logical, and character. Create matrices by attaching `dim` attributes to those vectors. Look up the help for `dimnames` and attach `dimnames` to these resulting matrices.

``` r
# Put your R code here.
int_v <- c(10L,1L,2L)
double_v <- c(10.1,10.2,10.3)
char_v <- c("a","b","c")
log_v <- c(TRUE,FALSE,F)

# Adding dim attributes - First Method
dim(int_v) <- c(1,3)
dim(double_v) <- c(1,3)
dim(char_v) <- c(1,3)
dim(log_v) <- c(1,3)

#second way of making matrices
matrix(int_v, c(1,3))
```

    ##      [,1] [,2] [,3]
    ## [1,]   10    1    2

``` r
matrix(double_v, c(1,3))
```

    ##      [,1] [,2] [,3]
    ## [1,] 10.1 10.2 10.3

``` r
matrix(char_v, c(1,3))
```

    ##      [,1] [,2] [,3]
    ## [1,] "a"  "b"  "c"

``` r
matrix(log_v, c(1,3))
```

    ##      [,1]  [,2]  [,3]
    ## [1,] TRUE FALSE FALSE

``` r
#dimnames
dimnames(int_v) <- list(c("r1"),c("Col1","Col2","Col3"))
int_v
```

    ##    Col1 Col2 Col3
    ## r1   10    1    2

``` r
dimnames(double_v) <- list(c("r1"),c("Col1","Col2","Col3"))
double_v
```

    ##    Col1 Col2 Col3
    ## r1 10.1 10.2 10.3

``` r
dimnames(char_v) <- list(c("r1"),c("Col1","Col2","Col3"))
char_v
```

    ##    Col1 Col2 Col3
    ## r1 "a"  "b"  "c"

``` r
dimnames(log_v) <- list(c("r1"),c("Col1","Col2","Col3"))
log_v
```

    ##    Col1  Col2  Col3
    ## r1 TRUE FALSE FALSE

1.  Create a list of length 4 and then add a `dim` attribute to it. What happens?

``` r
# Put your R code here.
l0=list(c(1,2,3,4),"ali",c(1L,2L),c(T,F))
length(l0)
```

    ## [1] 4

``` r
dim(l0) <- c(2,2)
l0
```

    ##      [,1]      [,2]     
    ## [1,] Numeric,4 Integer,2
    ## [2,] "ali"     Logical,2

``` r
typeof(l0)
```

    ## [1] "list"

``` r
# The list is showing in a matrix form of 2*2. It's type is list.
```

1.  Look up the help page for `data.frame` and use the example code to create a small data frame containing numeric variables and factors.

``` r
# Put your R code here.
month = c("March","April","January","November","January", 
 "September","October","September","November","August",
 "January","November","November","February","May","August",
 "July","December","August","August","September","November",
 "February","April")
fac_month = factor(month)
#fac_month
table(fac_month)
```

    ## fac_month
    ##     April    August  December  February   January      July     March 
    ##         2         4         1         2         3         1         1 
    ##       May  November   October September 
    ##         1         5         1         3

``` r
#levels(facmons)
L3 <- LETTERS[1:3]
d <- data.frame(7:30, seq(1,24), fac_month, sample(L3, 24, replace = TRUE))
d
```

    ##    X7.30 seq.1..24. fac_month sample.L3..24..replace...TRUE.
    ## 1      7          1     March                              B
    ## 2      8          2     April                              B
    ## 3      9          3   January                              A
    ## 4     10          4  November                              A
    ## 5     11          5   January                              C
    ## 6     12          6 September                              C
    ## 7     13          7   October                              C
    ## 8     14          8 September                              A
    ## 9     15          9  November                              A
    ## 10    16         10    August                              B
    ## 11    17         11   January                              C
    ## 12    18         12  November                              A
    ## 13    19         13  November                              A
    ## 14    20         14  February                              B
    ## 15    21         15       May                              B
    ## 16    22         16    August                              A
    ## 17    23         17      July                              C
    ## 18    24         18  December                              B
    ## 19    25         19    August                              B
    ## 20    26         20    August                              B
    ## 21    27         21 September                              A
    ## 22    28         22  November                              A
    ## 23    29         23  February                              B
    ## 24    30         24     April                              C

1.  Use the `seq` function to generate a subscript vector that selects those elements of a vector that have even-numbered subscripts.

``` r
# Put your R code here.
x <- 10:140

#First Method:
even <- which(x %% 2 == 0)
x[even]
```

    ##  [1]  10  12  14  16  18  20  22  24  26  28  30  32  34  36  38  40  42
    ## [18]  44  46  48  50  52  54  56  58  60  62  64  66  68  70  72  74  76
    ## [35]  78  80  82  84  86  88  90  92  94  96  98 100 102 104 106 108 110
    ## [52] 112 114 116 118 120 122 124 126 128 130 132 134 136 138 140

``` r
#Second Method:

for (i in seq(1,length(x)))
(if ( x[i] %% 2 == 0) print(x[i]) )
```

    ## [1] 10
    ## [1] 12
    ## [1] 14
    ## [1] 16
    ## [1] 18
    ## [1] 20
    ## [1] 22
    ## [1] 24
    ## [1] 26
    ## [1] 28
    ## [1] 30
    ## [1] 32
    ## [1] 34
    ## [1] 36
    ## [1] 38
    ## [1] 40
    ## [1] 42
    ## [1] 44
    ## [1] 46
    ## [1] 48
    ## [1] 50
    ## [1] 52
    ## [1] 54
    ## [1] 56
    ## [1] 58
    ## [1] 60
    ## [1] 62
    ## [1] 64
    ## [1] 66
    ## [1] 68
    ## [1] 70
    ## [1] 72
    ## [1] 74
    ## [1] 76
    ## [1] 78
    ## [1] 80
    ## [1] 82
    ## [1] 84
    ## [1] 86
    ## [1] 88
    ## [1] 90
    ## [1] 92
    ## [1] 94
    ## [1] 96
    ## [1] 98
    ## [1] 100
    ## [1] 102
    ## [1] 104
    ## [1] 106
    ## [1] 108
    ## [1] 110
    ## [1] 112
    ## [1] 114
    ## [1] 116
    ## [1] 118
    ## [1] 120
    ## [1] 122
    ## [1] 124
    ## [1] 126
    ## [1] 128
    ## [1] 130
    ## [1] 132
    ## [1] 134
    ## [1] 136
    ## [1] 138
    ## [1] 140

1.  Verify that vectors can have duplicated names and that if a subscript matches a duplicated name, only the first value is returned. What happens with `x[NA]`?

``` r
# Put your R code here.
x <- c(a1=1,a2=2,a1=3,a3=4)
names(x)
```

    ## [1] "a1" "a2" "a1" "a3"

``` r
x["a1"]
```

    ## a1 
    ##  1

``` r
#Only the first value is given back

x[NA]
```

    ## <NA> <NA> <NA> <NA> 
    ##   NA   NA   NA   NA

``` r
#NA are given back for both names and values by this command
```

1.  Use logical subscripts to extract the even-numbered elements of the `letters` vector.

``` r
# Put your R code here.

cc <- letters[1:10]
cc
```

    ##  [1] "a" "b" "c" "d" "e" "f" "g" "h" "i" "j"

``` r
#First Method
for(i in 1:length(cc))
  ( if (i%% 2==0) print(cc[i])
)
```

    ## [1] "b"
    ## [1] "d"
    ## [1] "f"
    ## [1] "h"
    ## [1] "j"

``` r
#Second Method
remove(vector)
```

    ## Warning in remove(vector): object 'vector' not found

``` r
for(i in 1:length(cc)) #c[1]:lenght(c)
if(i %% 2 == 0)
vector <- c(vector, cc[i])
vector
```

    ## [[1]]
    ## function (mode = "logical", length = 0L) 
    ## .Internal(vector(mode, length))
    ## <bytecode: 0x1b22718>
    ## <environment: namespace:base>
    ## 
    ## [[2]]
    ## [1] "b"
    ## 
    ## [[3]]
    ## [1] "d"
    ## 
    ## [[4]]
    ## [1] "f"
    ## 
    ## [[5]]
    ## [1] "h"
    ## 
    ## [[6]]
    ## [1] "j"

1.  Let `x` be a vector of length 10 generated by `1:10` and suppose it has a dimension attribute so that it is a matrix with 2 columns and 5 rows. What is the matrix location of the 7th element of `x`? That is, which row and column is it in? Alternatively, which element of `x` is in the second row, first column?

``` r
# Put your R code here.
x=1:10
dim(x) <- c(2,5)
x
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    1    3    5    7    9
    ## [2,]    2    4    6    8   10

``` r
x[7]
```

    ## [1] 7

``` r
# the 7th element is at the 1st row and 4th column and its value is 7. 

#========
#nrow(x)
#ncol(x)
x[2,1]
```

    ## [1] 2

``` r
#Element 6 is in the 2nd row 1st column

#====
# if I want to find which element of matrix is equal to 11 I can use this command
which(x  == 6)
```

    ## [1] 6

1.  What does `as.matrix()` do when applied to a data frame with columns of different types?

``` r
# Put your R code here.
L3 <- LETTERS[1:3]
d1 <- data.frame(1, 1:10, sample(L3, 10, replace = TRUE))
d1
```

    ##    X1 X1.10 sample.L3..10..replace...TRUE.
    ## 1   1     1                              B
    ## 2   1     2                              A
    ## 3   1     3                              A
    ## 4   1     4                              B
    ## 5   1     5                              B
    ## 6   1     6                              A
    ## 7   1     7                              B
    ## 8   1     8                              A
    ## 9   1     9                              C
    ## 10  1    10                              C

``` r
as.matrix(d1)
```

    ##       X1  X1.10 sample.L3..10..replace...TRUE.
    ##  [1,] "1" " 1"  "B"                           
    ##  [2,] "1" " 2"  "A"                           
    ##  [3,] "1" " 3"  "A"                           
    ##  [4,] "1" " 4"  "B"                           
    ##  [5,] "1" " 5"  "B"                           
    ##  [6,] "1" " 6"  "A"                           
    ##  [7,] "1" " 7"  "B"                           
    ##  [8,] "1" " 8"  "A"                           
    ##  [9,] "1" " 9"  "C"                           
    ## [10,] "1" "10"  "C"

``` r
#The elements of it will coerced to the most flexible type. According  to the help file, types from least to most flexible are: logical, integer, double, and character. So here d1's elements will be changed to char.
```

1.  Fix each of the following common data frame subsetting errors:

``` r
#mtcars[mtcars$cyl = 4, ]
#mtcars[-1:4, ]
#mtcars[mtcars$cyl <= 5]
#mtcars[mtcars$cyl == 4 | 6, ]

#Corrected Answer:

mtcars[mtcars$cyl == 4, ]
```

    ##                 mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Datsun 710     22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## Merc 240D      24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## Merc 230       22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## Fiat 128       32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## Honda Civic    30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## Toyota Corolla 33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## Toyota Corona  21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## Fiat X1-9      27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## Porsche 914-2  26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## Lotus Europa   30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## Volvo 142E     21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

``` r
mtcars[-c(1:4), ]
```

    ##                      mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
    ## Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
    ## Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
    ## Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
    ## Merc 280C           17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
    ## Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
    ## Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
    ## Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
    ## Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
    ## Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
    ## Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
    ## Fiat 128            32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## Honda Civic         30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## Toyota Corolla      33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## Toyota Corona       21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## Dodge Challenger    15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
    ## AMC Javelin         15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
    ## Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
    ## Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
    ## Fiat X1-9           27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## Porsche 914-2       26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## Lotus Europa        30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
    ## Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
    ## Volvo 142E          21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

``` r
mtcars[mtcars$cyl <= 5, ]
```

    ##                 mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Datsun 710     22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## Merc 240D      24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## Merc 230       22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## Fiat 128       32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## Honda Civic    30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## Toyota Corolla 33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## Toyota Corona  21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## Fiat X1-9      27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## Porsche 914-2  26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## Lotus Europa   30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## Volvo 142E     21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

``` r
mtcars[mtcars$cyl == 4 | mtcars$cyl == 6, ]
```

    ##                 mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## Mazda RX4      21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag  21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
    ## Datsun 710     22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive 21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
    ## Valiant        18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
    ## Merc 240D      24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
    ## Merc 230       22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
    ## Merc 280       19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
    ## Merc 280C      17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
    ## Fiat 128       32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
    ## Honda Civic    30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
    ## Toyota Corolla 33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
    ## Toyota Corona  21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
    ## Fiat X1-9      27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
    ## Porsche 914-2  26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
    ## Lotus Europa   30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
    ## Ferrari Dino   19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
    ## Volvo 142E     21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2

1.  Consider the linear model: `mod <- lm(mpg ~ wt, data = mtcars)`. Describe the data structure of `mod`, including its componets. Extract the coefficients, residuals, and the residual degrees of freedom. Extract the R squared from the model summary, i.e., from `summary(mod)`.

``` r
#  Put your R code here.
mod <- lm(mpg ~ wt, data = mtcars)
str(mod) # We can get information about the data structure by using this command line.After running the code it will provide all the information about the structure of different variables of mod. For example it is saying that there is a list of 12 elemnts. The first element in the list is a number of 2 and its name is coefficients. Then it shows its attributes' names in the following line. After that it is giving information about the residuals which is a consisted of 32 elements(numbers) and then their attributes' names and so on...
```

    ## List of 12
    ##  $ coefficients : Named num [1:2] 37.29 -5.34
    ##   ..- attr(*, "names")= chr [1:2] "(Intercept)" "wt"
    ##  $ residuals    : Named num [1:32] -2.28 -0.92 -2.09 1.3 -0.2 ...
    ##   ..- attr(*, "names")= chr [1:32] "Mazda RX4" "Mazda RX4 Wag" "Datsun 710" "Hornet 4 Drive" ...
    ##  $ effects      : Named num [1:32] -113.65 -29.116 -1.661 1.631 0.111 ...
    ##   ..- attr(*, "names")= chr [1:32] "(Intercept)" "wt" "" "" ...
    ##  $ rank         : int 2
    ##  $ fitted.values: Named num [1:32] 23.3 21.9 24.9 20.1 18.9 ...
    ##   ..- attr(*, "names")= chr [1:32] "Mazda RX4" "Mazda RX4 Wag" "Datsun 710" "Hornet 4 Drive" ...
    ##  $ assign       : int [1:2] 0 1
    ##  $ qr           :List of 5
    ##   ..$ qr   : num [1:32, 1:2] -5.657 0.177 0.177 0.177 0.177 ...
    ##   .. ..- attr(*, "dimnames")=List of 2
    ##   .. .. ..$ : chr [1:32] "Mazda RX4" "Mazda RX4 Wag" "Datsun 710" "Hornet 4 Drive" ...
    ##   .. .. ..$ : chr [1:2] "(Intercept)" "wt"
    ##   .. ..- attr(*, "assign")= int [1:2] 0 1
    ##   ..$ qraux: num [1:2] 1.18 1.05
    ##   ..$ pivot: int [1:2] 1 2
    ##   ..$ tol  : num 1e-07
    ##   ..$ rank : int 2
    ##   ..- attr(*, "class")= chr "qr"
    ##  $ df.residual  : int 30
    ##  $ xlevels      : Named list()
    ##  $ call         : language lm(formula = mpg ~ wt, data = mtcars)
    ##  $ terms        :Classes 'terms', 'formula' length 3 mpg ~ wt
    ##   .. ..- attr(*, "variables")= language list(mpg, wt)
    ##   .. ..- attr(*, "factors")= int [1:2, 1] 0 1
    ##   .. .. ..- attr(*, "dimnames")=List of 2
    ##   .. .. .. ..$ : chr [1:2] "mpg" "wt"
    ##   .. .. .. ..$ : chr "wt"
    ##   .. ..- attr(*, "term.labels")= chr "wt"
    ##   .. ..- attr(*, "order")= int 1
    ##   .. ..- attr(*, "intercept")= int 1
    ##   .. ..- attr(*, "response")= int 1
    ##   .. ..- attr(*, ".Environment")=<environment: R_GlobalEnv> 
    ##   .. ..- attr(*, "predvars")= language list(mpg, wt)
    ##   .. ..- attr(*, "dataClasses")= Named chr [1:2] "numeric" "numeric"
    ##   .. .. ..- attr(*, "names")= chr [1:2] "mpg" "wt"
    ##  $ model        :'data.frame':   32 obs. of  2 variables:
    ##   ..$ mpg: num [1:32] 21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
    ##   ..$ wt : num [1:32] 2.62 2.88 2.32 3.21 3.44 ...
    ##   ..- attr(*, "terms")=Classes 'terms', 'formula' length 3 mpg ~ wt
    ##   .. .. ..- attr(*, "variables")= language list(mpg, wt)
    ##   .. .. ..- attr(*, "factors")= int [1:2, 1] 0 1
    ##   .. .. .. ..- attr(*, "dimnames")=List of 2
    ##   .. .. .. .. ..$ : chr [1:2] "mpg" "wt"
    ##   .. .. .. .. ..$ : chr "wt"
    ##   .. .. ..- attr(*, "term.labels")= chr "wt"
    ##   .. .. ..- attr(*, "order")= int 1
    ##   .. .. ..- attr(*, "intercept")= int 1
    ##   .. .. ..- attr(*, "response")= int 1
    ##   .. .. ..- attr(*, ".Environment")=<environment: R_GlobalEnv> 
    ##   .. .. ..- attr(*, "predvars")= language list(mpg, wt)
    ##   .. .. ..- attr(*, "dataClasses")= Named chr [1:2] "numeric" "numeric"
    ##   .. .. .. ..- attr(*, "names")= chr [1:2] "mpg" "wt"
    ##  - attr(*, "class")= chr "lm"

``` r
summary(mod)  # We can get some information about the lm by using this command line
```

    ## 
    ## Call:
    ## lm(formula = mpg ~ wt, data = mtcars)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -4.5432 -2.3647 -0.1252  1.4096  6.8727 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  37.2851     1.8776  19.858  < 2e-16 ***
    ## wt           -5.3445     0.5591  -9.559 1.29e-10 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 3.046 on 30 degrees of freedom
    ## Multiple R-squared:  0.7528, Adjusted R-squared:  0.7446 
    ## F-statistic: 91.38 on 1 and 30 DF,  p-value: 1.294e-10

``` r
mod$df.residual
```

    ## [1] 30

``` r
residuals(mod) #or  mod$residual
```

    ##           Mazda RX4       Mazda RX4 Wag          Datsun 710 
    ##          -2.2826106          -0.9197704          -2.0859521 
    ##      Hornet 4 Drive   Hornet Sportabout             Valiant 
    ##           1.2973499          -0.2001440          -0.6932545 
    ##          Duster 360           Merc 240D            Merc 230 
    ##          -3.9053627           4.1637381           2.3499593 
    ##            Merc 280           Merc 280C          Merc 450SE 
    ##           0.2998560          -1.1001440           0.8668731 
    ##          Merc 450SL         Merc 450SLC  Cadillac Fleetwood 
    ##          -0.0502472          -1.8830236           1.1733496 
    ## Lincoln Continental   Chrysler Imperial            Fiat 128 
    ##           2.1032876           5.9810744           6.8727113 
    ##         Honda Civic      Toyota Corolla       Toyota Corona 
    ##           1.7461954           6.4219792          -2.6110037 
    ##    Dodge Challenger         AMC Javelin          Camaro Z28 
    ##          -2.9725862          -3.7268663          -3.4623553 
    ##    Pontiac Firebird           Fiat X1-9       Porsche 914-2 
    ##           2.4643670           0.3564263           0.1520430 
    ##        Lotus Europa      Ford Pantera L        Ferrari Dino 
    ##           1.2010593          -4.5431513          -2.7809399 
    ##       Maserati Bora          Volvo 142E 
    ##          -3.2053627          -1.0274952

``` r
coefficients(mod) # or mod$coefficients
```

    ## (Intercept)          wt 
    ##   37.285126   -5.344472

``` r
summary(mod)$r.squared
```

    ## [1] 0.7528328
