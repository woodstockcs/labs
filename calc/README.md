# Calc

## What to do?

Implement a program that implements a command line calculator.

```
$ ./calc 50 x 28
1400.000000
```

{% next %}

## Divide and Conquer
In this problem, you will be tasked with implementing a very simple command-line based calculator program. Your program will accept inputs like this (wherein underlined text represents user input):

```
$ ./calc 4 + 5
9.000000
```

or, indeed like this (allowing the user to perform some basic floating-point arithmetic)

```
$ ./calc 8.38 - 5.12
3.260000
```
such that the user can perform all five of the basic math operations that C permits — addition, subtraction, multiplication, division, and modulo.

Notice that unlike many other programs you’ve likely written up to this point, and just like Old Friends, users are not entering any information after the program has started running. Rather, they are providing all of their input to the program at the command line, before the program has begun.

{% next %}

## Implementation Details

Recall that if we collect information from the user at the command line, we can use two special parameters passed into main (conventionally called argc and argv) which represent the number of arguments the user provided and the actual data the user provided, respectively. Given the example use case above, how many command-line arguments is the user expected to provide?

If they fail to provide the correct number, your program should exit (possibly printing out an error message that tells them how they should have run the program) and return 1; so that we can automate testing of your code.

Assuming we have the right number of command-line arguments, we’re well on our way. There’s a catch, though.

Just because the user types a real number at the command line, that doesn’t mean their input will be automatically stored in a float. Actually, it will be stored as a string that just so happens to look like an float; after all, remember the data type of argv? It’s an array where each element is a string! And so you’ll need to convert that string to an actual float. As luck would have it, a function, atof, exists for exactly that purpose! Here’s how you might use it:

```c
float a = atof(argv[1]);
```

There are two values that need to be converted from a string to a float (argv[1] and argv[3], specifically). So that just leaves dealing with the operator. Recall from the shorts on arrays and strings that a string in C is really just an array of characters. And we can access individual elements of an array by using square bracket notation to index into that array.

```c
string s = "Calculator";
printf("%c\n", s[0]); // prints 'C'
```

Similarly, if we have another string which just so happens to be called argv[2] can we index into its first element, which will be a single character (char).

```c
printf("%c\n", argv[2][0]); // prints the first character of argv[2]
```

And that also means we can compare argv[2][0] against a variety of possible values (such as +, -, x, / or %, for example) and make certain decisions in our program based on what that character is, perhaps by making use of some Boolean expressions and conditional statements. (Of course, since there are only a small number of characters that we care about in argv[2][0], you might also find this a good opportunity to use a switch statement for perhaps the first time.)

Note above that we suggest using a lowercase x instead of the typical asterisk used to represent multiplication. The reason for that is that the asterisk means something special at the command line, and so ordinarily it will not be processed correctly. So just be sure when you encounter an x at the command line that you actually perform a multiplication!

Once you’ve performed the arithmetic, just print out the result to the user on its own line, so we can automate testing of your code. By default, C will print out floating point values to six decimal places. Might as well leave it that way, there’s plenty to do otherwise in this problem!

{% next %}

## Implementation Details

Design and implement a program, initials, that, given a person’s name, prints a person’s initials.

Implement your program in a file called initials.c.

Your program should prompt a user for their name using get_string to obtain their name as a string.

You may assume that the user’s input will contain only letters (uppercase and/or lowercase) plus single spaces between words. You don’t need to worry about names like Joseph Gordon-Levitt, Conan O’Brien, or David J. Malan!

Your program should print the user’s initials (i.e., the first letter of each word in their name) with no spaces or periods, followed by a newline (\n).

You may assume that the only spaces in the user’s input will be single spaces between words.

## Pseudocode

First, write in pseudocode.txt at right some pseudocode that implements this program, even if not (yet!) sure how to write it in code. Remember a computer cannot see the entire name at one time like a human. Your program will have to analyze the name one character at a time.

{% spoiler "Spoiler" %}

1. Start out by using get_string() to promts a user for a name.
1. Print out the first character of the name as an upper case char.
1. Then iterate through the remaining characters of the string.
    1. Does the char you are looking at tell you then next char is an initial? If so, print out the next char using upper case.

{% endspoiler %}


{% next %}

## Usage

Your program should behave per the examples below. 

```
$ ./initials
Zamyla Chan
ZC
```

```
$ ./initials
robert thomas bowden
RTB
```

{% spoiler "Hints" %}

To iterate through a string, use a for loop like this:

```c
for (int i = 0; i < strlen(s); i++)
{
  // do something
}
```

{% endspoiler %}

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2018/ap/initials/less
```

To make sure you get 5/5 for style, you may want to execute style50 first.

```
style50 initials.c
```


