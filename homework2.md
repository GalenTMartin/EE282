## Homework 2, 10/15/2018

### Question 1
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

*_To be frank, I'm actually not certain what constitutes a script. This is a collection of commands, and as far as I know that's what constitutes a script_

### Question 2
