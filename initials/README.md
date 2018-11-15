# Initials

## tl;dr

Implement a program that, given a person’s name, prints a person’s initials, per the below.

```
$ ./initials
Regulus Arcturus Black
RAB
```

{% next %}

## Getting Ready

First, take a self-paced tour through a few coding examples that are likely to prove quite useful to you as you work on this and some future problems in this unit, the source code for which can be found at http://bit.ly/2zPo948.

Here is the first of those videos.

{% video https://www.youtube.com/watch?v=BYbuuUntOZ4&feature=youtu.be&list=PLhQjrBD2T380sc-fXwl1sviA-twxFduVU %}

Others can be found at: 

{% next %}

## Implementation Details

Design and implement a program, initials, that, given a person’s name, prints a person’s initials.

Implement your program in a file called initials.c.

Your program should prompt a user for their name using get_string to obtain their name as a string.

You may assume that the user’s input will contain only letters (uppercase and/or lowercase) plus single spaces between words. You don’t need to worry about names like Joseph Gordon-Levitt, Conan O’Brien, or David J. Malan!

Your program should print the user’s initials (i.e., the first letter of each word in their name) with no spaces or periods, followed by a newline (\n).

{% spoiler "Hints" %}

{% video https://www.youtube.com/watch?v=DCVu-BIV_tw %}

First you'll prompt for the days in the month. If the user does not type in 28, 29, 30, or 31, the program should prompt the user to retry.

Then you'll prompt for pennies on the first day. This must be a positive integer.

Do you remember how to validate user input?

{% video https://www.youtube.com/watch?v=LxvTJMYtRnU %}

Remember you'll have to keep track of your total pennies due in a long long, as per the spec above. You can declare a long long like this:

```
long long total;
```

and initialze it by assigning it a starting value.

Now you'll have to add to that total the pennies you get on day 2, day 3, and so on until you've added pennies for every day of the month. You can use the function:

```c
pow(2, n)
```
in the math.h library if you want to use 2 to some power of n in you calculation. And of course print out your grand total as dollars and cents, with a dollar sign in front, and exactly two decimal places.

Watch Zamyla's video below for a bit more help! And you may just want to jot down her pseudocode!

{% video https://www.youtube.com/watch?v=QoxUQjXiZv0 %}

{% endspoiler %}


### How to Test Your Code

Does your code work as prescribed when you input

* `32` (or more for days)?
* `-1` (for pennies on day 1)?
* no input at all for either prompt, when you only hit Enter?

Here are some values to check for:

* 28 days, 1 penny on day one yields $2684354.55
* 31 days, 1 penny on day one yields $21474836.47
* 29 days, 2 pennies on day one yields $10737418.22
* 30 days, 30 pennies on day one yields $322122546.90

Are your results exactly the same?

{% next %}

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2018/ap/pennies
```

To make sure you get 5/5 for style, you may want to execute style50 first.

```
style50 pennies.c
```


