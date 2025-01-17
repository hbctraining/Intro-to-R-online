## Introduction

Welcome to segment 2C, Introduction to Complex Data Structures. In segment 2B, we got comfortable with the idea of using vectors and factors as variables for storing one-dimensional data, and we discussed how they can be used as building blocks for creating other, higher dimensional, data structures in R. In this lesson, we will explore the data structures for two-dimensional data, including matrices and data frames. In addition, we will introduce a data structure called a list for storing many different objects.

## Matrix

The first two-dimensional data structure we will introduce is called a matrix. A `matrix` in R is essentially a vector divided into a certain number of rows and columns. 

![matrix](../img/matrix.png)

For instance, we could create a matrix using the `matrix()` function, and have a vector of values from number 1 to 6 be divided between 2 rows and 3 columns.

```r
# Create a vector to be turned into a matrix
top_num <- c(1,2,3,4,5,6)

# Turn vector into matrix
mx <- matrix(top_num, nrow = 2, ncol = 3)
mx
```

Once the matrix is created, each row and each column could be thought of as a vector of values of the same length with all of the columns and rows having the same data type.

Matrices are used commonly as part of the mathematical machinery of statistics. They are usually of numeric or integer data type and used in computational algorithms to serve as a checkpoint. For example, if input data is not of identical data type (numeric, character, etc.), the `matrix()` function will throw an error and stop any downstream code execution.

While matrices are usually numeric, they can also be created using any of the other data types. You can have matrices with all character or all logical values, as well.

### Data Frame

The next two-dimensional data structure we will explore is the data frame. A `data.frame` is the _de facto_ data structure for most tabular data and what we use for statistics and plotting. A `data.frame` is similar to a matrix in that it's a collection of vectors of the **same length** and each vector represents a column. However, in a data frame **each vector can be of a different data type** (e.g., characters, integers, factors). 

![dataframe](../img/dataframe.png)

In this data frame, the first column is of the `character` data type, the second column is numeric, the third is character, and the fourth is logical.

A data frame is the most common way of storing data in R, and if used systematically makes data analysis easier. 

We can create a data frame by bringing **vectors** together to **form the columns**. We do this using the `data.frame()` function, and giving the function the different vectors we would like to bind together. *This function will only work for vectors of the same length.*

Let's create a data frame called `df`. We can do this by typing `data.frame`, parentheses, and inside the parentheses adding the names of the vectors that we would like to turn into columns, in the order we would like them to appear. So we will type `species`, comma, `glengths`. Then we can use the assignment operator to create a variable called `df`. 

```r
# Create data frame
df <- data.frame(species, glengths)
```

We can see that a new variable called `df` has been created in our environment within a new section called `Data`. In the environment, it specifies that `df` has 3 observations of 2 variables. What does that mean? In R, rows always come first, so it means that `df` has 3 rows and 2 columns. We can get additional information if we click on the blue circle with the white triangle in the middle next to `df`. It will display information about each of the columns in the data frame, giving information about what the data type is of each of the columns and the first few values of those columns.

Note that the species column is now a factor even though we added it as a character vector. It turns out that the `data.frame()` function will turn all **character vectors into factors** by default. There are ways that we can change the default behavior of the function as we will see in Segment 3A, but we will leave it as is for now. 

Another handy feature in RStudio is that if we hover the cursor over the variable name, `df`, it will turn into a pointing finger. If you click on `df`, it will open the data frame as it's own tab next to the script editor. We can explore the table interactively within this window. To close, just click on the X on the tab.

As with any variable, if we type the variable's name and run, we can print the values stored inside to the console . Let's type and run `df`.

```r
df
```

### Lists

Now we'll move on to the list data structure. Lists are a data structure in R that can be perhaps a bit daunting at first, but soon become amazingly useful. We will discuss how lists can be useful after we understand a bit more about how they are structured.

A list is a data structure that can hold any number of any types of other data structures.

![list](../img/list.png)


If you have variables of different data structures you wish to combine, you can put all of those into one list object by using the `list()` function and placing all the items you wish to combine within parentheses. 

Let's create a list called `list1`, which contains as components the `species` vector, the `df` data frame, and the single value, `number`. We'll type `list1`, arrow, then the `list()` function. In parentheses, include `species`, `df`, and `number`.

```r
# Create a list
list1 <- list(species, df, number)
```

We see `list1` appear within the Data section of our environment as a list of 3 components or variables. If we click on the blue circle with a triangle in the middle, it's not quite as interpretable as it was for data frames. Essentially, each component is preceded by a colon. The first colon gives the `species` vector, the second colon precedes the `df` data frame, with the dollar signs indicating the different columns, the last colon gives the `number` variable.

If I click on `list1`, it opens a tab where you can explore the contents a bit more, but it's still not super intuitive. The easiest way to view small lists is to print them to the console. 

Let's type `list1` and print out the contents to the console by running it.

```r
list1
```

There are three components corresponding to the three different variables we passed in, and what you see is that structure of each is retained. We can see that the first component of the list, `species`, is denoted by a double-bracket 1. The second component with double-bracket 2, and the third component with double-bracket 3. 

Now that we know what lists are, why would we ever want to use them? When getting started with R, you will most likely encounter lists with different tools or functions that you use. Oftentimes a tool will need a list as input, so that all the information needed to run the tool is present in a single variable. Sometimes a tool will output a list when working through an analysis. Knowing how to work with them and extract necessary information will be critically important. 

As you become more comfortable with R, you will find yourself using lists more often. One common use of lists is to make iterative processes more efficient. For example, let's say you had multiple data frames containing the same weather information from different cities throughout North America. You wanted to perform the same task on each of the data frames, but that would take a long time to do individually. Instead you could create a list where each data frame is a component of the list. Then, you could perform the task on the list instead, which would be applied to each of the components.

## Conclusion

Understanding the fundamentals of the most basic data structures in R will be helpful when performing many of the most basic data science operations, such as reading in, exploring, and wrangling data within R. Hopefully, you have a basic understanding of the structure of matrices, data frames, and lists and why we would use them. Also, hopefully, you can describe the similarities and differences between the two-dimensional data structures, matrices and data frames. 

To summarize, in this lesson, we explored the **matrix**, **data frame**, and **list** data structures available to us in R. We learned how to create these data structures, as well as, explored when these data structures are useful. 

---

*This lesson has been developed by members of the teaching team at the [Harvard Chan Bioinformatics Core (HBC)](http://bioinformatics.sph.harvard.edu/). These are open access materials distributed under the terms of the [Creative Commons Attribution license](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0), which permits unrestricted use, distribution, and reproduction in any medium, provided the original author and source are credited.*

* *The materials used in this lesson are adapted from work that is Copyright © Data Carpentry (http://datacarpentry.org/). 
All Data Carpentry instructional material is made available under the [Creative Commons Attribution license](https://creativecommons.org/licenses/by/4.0/) (CC BY 4.0).*


