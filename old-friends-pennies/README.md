# Old Friends: Pennies

In Pennies you were asked to write a program that demonstrated the power of exponentiation by showing how much money you would have if a person gave you x pennies on a particular day, and then doubled the amount they gave you every day for a period of y days.

```
$ ./pennies
Days in month: 31
Pennies on first day: 1
$21474836.47
```
As you might expect, we’d now like the program to work as follows.

```
$ ./pennies 31 1
$21474836.47
```


{% next %}

## Makin' Bank

Notice a few differences with this program from the previous two. How many command line arguments does this one accept? Be sure to modify your check against argc accordingly. And also know that in stdlib.h alongside of the function atof exists another, atoi, that converts a string to an int in much the same way that atof converts a string to a float.

Incidentally, you can assume that the user will only type integers at the command line; there’s no need for you to anticipate a rogue user this time around!

{% next %}

## Implementation

Before starting to modify this program, think about how you will validate the number of days and starting pennies. You probably don't want to reprompt. Better to include a check that the days and pennies are in an acceptable range and print out an error messsage and return 1 if they are not.

What else do you need to do?

{% spoiler "Pseudocode" %}
1. Remember to change the main function to accept command line arguments.
1. Check for the correct number of command line arguments. Print a usage message and return 1 if not correct.
1. Change the do while loops so that incorrect inputs do not reprompt. Use if statements similar to the command line check to insure days are in the range [28, 31] and pennies is a positive number.
1. You do not have to change the algorithm that calculates or prints out the total pennies. 
1. Compile and run!

{% endspoiler %}


{% next %}

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2018/ap/friends/pennies
```
## Style

```
style50 pennies.c
```



