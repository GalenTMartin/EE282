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

### Question 1 Comments:
Very well done. I just a few suggestions. instead of cd dirgalentm you can just do cd dir$USER or cd dir${USER} the last example being an explicit call to the variable user, and the method I recommend just because your variable will work everytime, even if it is quotes. for the mkdir command, I recommend using -p option incase the directory already exists, it won't throw an error. for rmdir, rmdir will only work if the directory is empty, otherwise you will need to run rm -rf dir2.

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

### Question 3 (option 2)
In your home directory, create a new directory named "chmodtestdir" and add a file to this directory named "chmodtest." The file should be a script, executable by everyone but only writeable by the creator, which prints "Permissions are fun!" to the screen.

#### Question 3 Answers
The following commands are needed to create the directory and file
```
mkdir chmodtestdir
cd chmodtestdir
touch chmodtest
```

Now, to ensure that the file is readable and executable, we must make sure that the parent directory is executable:
```
#First I'll go back to the home directory:
cd
#now I'll check permissions
ls -l 
#By default the directory should be executable for everyone, but if not use
chmod ugo+x chmodtestdir
```
Now we can make the file we've touched "chmodtest" the requested script.
```
cd chmodtestdir
vi chmodtest
```
Inside the editor, we add the line:
```
echo "Permissions are fun!"
```
Then hit the esc button and :wq to save and exit.

Finally, we must make the script readable and executable and check our permissions using ls -l:
```
chmod 755 chmodtest
ls -l
```
ls -l should give permissions for chmodtest as rwxr-xr-x, meaning those in group and other can only read and execute, not write.

### Question 3 Comments:
Also very well done. One suggestion though, you can do chmod +x chmodtestdir also, as it implies that +x is added to all. Also when you cd on line 105, I suggest you do cd ../ because cd does nothing if there is no arguement proceeding it. you could also not cd back up and just do chmod +x ../chmodtestdir and avoid having to jump back and forth between directories.
