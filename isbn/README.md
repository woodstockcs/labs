# ISBN

{% video https://www.youtube.com/watch?v=AJ9MFMQbhhw %}

{% next %}

## What to do

Implement a program to validate ISBN-10 numbers.

```
./isbn
ISBN: 0307476464
YES
```

{% next %}

## Readin' Bookz

As you may know, most any book that you borrow or buy has an International Standard Book Number, otherwise known as an ISBN or ISBN-10, "a 10-digit number that uniquely identifies books and book-like products published internationally." Books published since 2007 might also have an ISBN-13, a 13-digit number with a similar purpose, but never mind those.

It turns out that the last of an ISBN-10’s digits is a "check digit," otherwise known (in binary contexts) as a "checksum," a number related mathematically to its preceding digits. ISBN-10s' digits are supposed to adhere to a formula, not unlike credit card numbers, and this check digit allows you to check whether an ISBN-10’s other nine digits are (most likely) valid without having to check, say, a database of books.

Per the International ISBN Agency’s ISBN Users' Manual, "The check digit is the last digit of an ISBN. It is calculated on a modulus 11 with weights 10-2, using X in lieu of 10 where ten would occur as a check digit."

{% next %}

Yes, but what does that mean? The manual elaborates. "This means that each of the first nine digits of the ISBN—​excluding the check digit itself—​is multiplied by a number ranging from 10 to 2 and that the resulting sum of the products, plus the check digit, must be divisible by 11 without a remainder."

Okay, better, but still a bit unclear. Let’s define the check digit in terms of a formula. Fortunately, thanks to "modular arithmetic," we can simplify the Agency’s formal definition using weights ranging from 1 to 9 instead of 10 to 2. In fact, it’s really quite simple. If x<sub>1</sub> represents an ISBN-10’s first digit (aka the left-most digit) and x<sub>10</sub> its last digit (aka the right-most digit), it turns out that:

x<sub>10</sub> = (1·x<sub>1</sub> + 2·x<sub>2</sub> + 3·x<sub>3</sub> + 4·<sub>x4</sub> + 5·x<sub>5</sub> + 6·x<sub>6</sub> + 7·x<sub>7</sub> + 8·x<sub>8</sub> + 9·x<sub>9</sub>) mod 11

In other words, to compute an ISBN-10’s tenth digit, multiply its first digit by 1, its second digit by 2, its third digit by 3, its fourth digit by 4, its fifth digit by 5, its sixth digit by 6, its seventh digit by 7, its eighth digit by 8, and its ninth digit by 9. Take the sum of those products and then divide it by 11. The remainder should be the ISBN-10’s tenth digit! If, though, that remainder is 10, the tenth digit should instead be printed as X lest it be confused with a 1 followed by 0.

{% next %}

## I S BN Calculatin'

Let’s try all this out. The ISBN-10 for the *Absolute Beginner’s Guide to C*  is 0-789-75198-4, the tenth digit of which is, obviously, 4. But is the syllabus right? Well, let’s first take that sum using the ISBN-10’s first nine digits (highlighted in bold):

1·**0** + 2·**7** + 3·**8** + 4·**9** + 5·**7** + 6·**5** + 7·**1** + 8·**9** + 9·**8** = 290

If we now divide that sum by 11, we get 290 ÷ 11 = 26 4/11 (i.e., a remainder of 4)! Well that’s kind of neat, the ISBN is legit! Actually, also thanks to modular arithmetic, we could just include that tenth digit in our sum and multiply it by 10:

1·**0** + 2·**7** + 3·**8** + 4·**9** + 5·**7** + 6·**5** + 7·**1** + 8·**9** + 9·**8** + 10·**4** = 330

If we now divide this sum by 11, we get 330 ÷ 11 = 30 with no remainder at all, which is an equivalent way of saying the ISBN-10 is legit! Stated more formally, 0 ≡ 330 (mod 11)!

Hopefully those exclamation points make the math more exciting.

So, computing this check digit’s not hard, but it does get a bit tedious by hand. Let’s write a program.

{% next %}

## Implementation Details

In a file named isbn.c, write a program that prompts the user for an ISBN-10 and then reports (via printf) whether the number’s legit. So that we can automate some tests of your code, we ask that your program’s last line of output be either YES\n or NO\n, nothing more, nothing less.

For simplicity, you may assume that the user’s input will be exactly ten decimal digits (i.e., devoid of hyphens and X), the first of which might even be zero(es), as in the case of our recommended book. But do not assume that the user’s input will fit in an int! Recall, after all, that the largest value that can fit in an int is 2<sup>32</sup> - 1 = 4,294,967,295 (and, even then, only if declared as unsigned). True, that’s a 10-digit value, but there might still be a problem. (What?) Best to be safe and use get_long from CS50’s library to get users' input. (Why?)

Okay, so you’ve gotten some input. What should you do? Well, realize that this C program, not unlike Scratch projects, can be reduced to the most basic of building blocks. For the sake of discussion, suppose that some variable x contains a 10-digit long (with no leading zeroes). How can you get at its tenth (i.e., rightmost) digit? Well how about this?

```c
int tenth = x % 10;
```

Do you see why that works? Do not pass Go until it dawns on you why!

How, now, can you get at that same variable’s ninth digit? Well, why don’t we first get rid of its tenth digit by shifting every other one place to the right?

```c
x = x / 10;
```

How about that trick? Do you see why it works? The ninth digit, now, is just:

```c
int ninth = x % 10;
```

{% next %}

So we bet there’s a pattern here. And odds are you don’t need to (i.e., shouldn’t) copy/paste lines like the above nine or ten times. Loops are your friend. To be sure, other approaches exist. Proceed as you wish! Perhaps some of these tricks, though, will get you started.

To compile your program, type

```
make isbn
```

Assuming your program compiled without errors (or, ideally, warnings) via either command, run your program with the command below.

```
./isbn
```

Consider the below representative of how your own program should behave when passed a valid ISBN-10 (sans hyphens); underlined is some user’s input.

```
$ ./isbn
ISBN: 0789751984
YES
```

Of course, get_long(“ISBN: “) itself will reject an ISBN-10’s hyphens (and more) anyway:

```
$ ./isbn
ISBN: 0-789-75198-4
Retry: foo
Retry: 0789751984
YES
```

But it’s up to you to catch inputs that are not ISBN-10s (e.g., [Jenny’s](https://en.wikipedia.org/wiki/867-5309/Jenny) phone number), even if ten digits.

```
$ ./isbn
ISBN: 5558675309
NO
```

{% next %}

### How to Test Your Code

Here are some values to check for:

* Beginners Guide (0789751984) valid
* Beginners Guide fake (0789751985) invalid
* Programming in C (0321776410) valid
* Jennys number (6178675309) invalid

Are your results exactly the same?

{% next %}

### Staff's Solution

To try out the staff's implementation of this problem, execute

```
./isbn
```

within [this sandbox](http://bit.ly/2NQ36U4).

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/problems/2019/ap/isbn
```

After submitting your code, be sure to check your score on [me50](https://submit.cs50.io). If you don't have full credit on you check50 grade, make the necessary updates and resubmit. You are free to resubmit as many times as you like.

***have some extra time?***

See that score for **style50**? It's a decimal number 0.00 - 1.00 listed right next to the check50 score. Click the style50 link and have a look at what it suggests for updates. Try to get it up to a score of 1.00! You are free to resubmit as many times as you like.

