## Homework 2, 10/15/2018

### Question 1 (option 1)
Ensure that you are in Galen's public directory by using the command 

```
cd /pub/galentm
```

Then, create a new directory named with your username using the command

```
mkdir dir$USER
```

Now move into the new directory you have created and create three new directories named dir1, dir2, and dir3.

Delete dir2, and then move back to /pub/galentm **without typing more than 5 characters.** 

#### Question 1 Answers
A script* which would execute all of the actions is as follows:

```
cd /pub/galentm
mkdir dir$USER
cd dirgalentm
#the command above will change depending on user
mkdir dir1 dir2 dir3
rmdir dir2
cd ..
```

*_To be frank, I'm actually not certain what constitutes a script. This is a collection of commands, and as far as I know that's what a script is_

### Question 2 (option 1)
Mr. Gould, a third grade teacher, wants to find the class average for a certain assignment using R. Not quite knowing how to begin, he creates an Excel spreadsheet of his class data (saved as "gradebook.csv") and separately enters the data into R manually to create a matrix.

The code he uses to import these data is as follows:

```{r}
#To create a matrix:
Student <- c("Jimmy", "Bobby", "Billy", "Roger", "Tanya", "Bjorn", "Tammy", "Phillis", 
              "Reggie", "Charlie", "Mikey", "Linda")
Number <- 1:12
Grade <- c(92,84,88,99,94,63,81,90,76,68,42,74)
grademat <- cbind(Student, Number, Grade)

#To import dataframe from Excel:
gradedf <- read.csv('gradebook.csv', header = TRUE)
```
To find the class average, Mr. Gould will need to use one of the following four commands in order to subset the grades from irrelevant information:

```{r}
grademat[,3]
gradedf[,3]
gradedf[3]
gradedf[[3]]
```

Which should he use, and why not the others? Provide a short script which will find the mean for him.

#### Question 2 Answers
Mr. Gould can use either 
```{r}
gradedf[,3] 
#or 
gradedf[[3]] 
```

He cannot use
```
grademat[,3]
```
because it provides the grades from the matrix. Matrices in R can only hold one kind of data, and because the matrix contains names, R turns the grade information from numerical data to character data. 

Similarly, he cannot use 
```{r}
gradedf[3]
```
because it doesn't return the data in vector form but keeps it as a single-column data frame. This data frame can't be processed using the "mean" function of R (I think).

To find the mean:
```{r}
justgrades <- gradedf[,3]
mean(justgrades)
```

### Question 3 (option 1)
