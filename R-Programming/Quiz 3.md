# R Programming Quiz 3
======

|Attempts|Score|
|--------|-----|
|     1/3|  5/5|


Question 1
----------
Take a look at the 'iris' dataset that comes with R. The data can be loaded with the code:

```
library (datasets)
data(iris)
```
There will be an object called 'iris' in your workspace. In this dataset, what is the mean of 'Sepal.Length' for the species virginica? (Please only enter the numeric result and nothing else.)

### Answer
6.588

### Explanation
```
library(datasets)
data(iris)
head(iris)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
tapply(iris$Sepal.Length, iris$Species, mean)
 setosa versicolor  virginica 
     5.006      5.936      6.588 
```
Question 2
----------
Continuing with the 'iris' dataset from the previous Question, what R code returns a vector of the means of the variables 'Sepal.Length', 'Sepal.Width', 'Petal.Length', and 'Petal.Width'?

### Answer
apply(iris[, 1:4],2,mean]

### Explanation

Apply is used to evaluate a function over the rows and columns of a dataset, matrix, or array. 

Iris is the dataset and we want the means of each column. The 2 indicates that we want to means of each column (Margin), mean is the function. Generally speaking, the apply() function has three elements:

    - 1. x as an array
    - 2. Margin is an integer vector indicating which margins should be retained. 1 corresponds to row, and 2 corresponds to          columns. 

Question 3
----------
Load the 'mtcars' dataset in R with the following code
```
library(datasets)
data(mtcars)
```
There will be an object names 'mtcars' in your workspace. You can find some information about the dataset by running
```
?mtcars
```
How can one calculate the average miles per gallon (mpg) by number of cylinders in the car (cyl)?

### Answer
```
tapply(mtcars$mpg, mtcars$cyl, mean)
with(mtcars, tapply(mpg, cyl, mean)
```
### Explanation
tapply is used to apply a function over subsets of a vector. Example, if you want to find the average age by gender in a dataset. tapply has five elements:

    - 1. x is a vector. 
    - 2. INDEX is a factor or a list of factors. IN this example the INDEXES are the variables we're measuring 
    - 3. FUN is a function to be applied
    - 4. ...contains other arguments to be passed through to the FUN
    - 5. Simply is a logical argument whose default is "TRUE" 
    
Question 4
----------
Continuing with the 'mtcars' dataset from the previous Question, what is the absolute difference between the average horsepower of 4-cylinder cars and the average horsepower of 8-cylinder cars?

### Answer
126.559

### Explanation
```
> hp <- tapply(mtcars$hp, mtcars$cyl,mean)
> hp
        4         6         8 
 82.63636 122.28571 209.21429 
> abs(hp[[1]] - hp[[3]])
[1] 126.5779
```
OR

```
abs(mean(mtcars[mtcars$cyl==4,]$hp) - mean(mtcars[mtcars$cyl==8,]$hp))
```
Question 5
----------
If you run
```
debug(ls)
```
what happens when you next call the 'ls' function?

### Answer

Execution of 'ls' will suspend at the beginning of the function and you will be in the browser.
