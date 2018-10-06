# Pennies

{% video https://www.youtube.com/watch?v=J6NVOMCV3W0 %}

{% next %}

## What to do

Implement a program that calculates the sum of getting a doubled amount of money each day for a month, as below.

```
$ ./pennies
Days in month: 30
Pennies on first day: 1
$10737418.23
```

{% next %}

## Double or Nothing

If ever given the choice between $10,000,000 or a month’s worth of pennies, whereby you receive a penny the first day, two pennies the second, four pennies the third, and so forth…​ take the pennies[1].

Anyhow, why the pennies? Exponentiation. Those pennies add up Consider how many pennies you’d receive on the 31st day alone, not to mention on the days leading up to it:

```
1 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2
  × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2
  × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2 × 2

  = 1073741824
```

Put more succinctly, that’s 1 × 2<sup>30</sup>. Convert those pennies to dollars (by dividing by 100) and you get, what, over $10,000,000? On just that day? Crazy.

What if you were given more than one penny on that first day? Or the month were February, in which case you’d get shortchanged a few million? (Best to take the pennies in January, March, May, July, August, October, or December.) Let’s find out.

{% next %}

## Implementation Details

Implement, in a file called pennies.c, a program that first asks the user how many days there are in the month and then asks the user how many pennies he or she will receive on the first day of that month. The program should then calculate the amount that the user will have received in total by the end of the month (not just on the last day) if that amount is doubled on every day but the first, expressed not as pennies but as dollars and cents. If the user does not type in 28, 29, 30, or 31 for the number of days in the month, the program should prompt the user to retry. If the user does not input a positive integer for the first day’s number of pennies, the program should prompt the user to retry.

For instance, your program might behave as follows, whereby underlined text represents some user’s input.

```
~/workspace/unit1/pennies/ $ ./pennies
Days in month: 32
Days in month: 31
Pennies on first day: 1
$21474836.47
```

Notice how this output suggests that the program should indeed re-prompt the user if he or she fails to cooperate with these rules (as by inputting too many days).

How to begin? Odds are you’ll want a couple of loops, one with which to prompt (and potentially re-prompt) the user for a number of days, and another with which to prompt (and potentially re-prompt) the user for a number of first-day pennies. How to get both those numbers? Perhaps the CS50 Library offers some options? You may also find functions in the math.h header file that can help when working on this problem. Have a look at [Reference50](https://reference.cs50.net/) to see which functions those might be. Be sure, if you use any of those functions, to place this line of code near the top of your pennies.c file:

```c
#include <math.h>
```

## Implementation Details

Implement, in `cash.c` at right, a program that first asks the user how much change is owed and then prints the minimum number of coins with which that change can be made.

* Use `get_float` to get the user's input and `printf` to output your answer. Assume that the only coins available are quarters (25¢), dimes (10¢), nickels (5¢), and pennies (1¢).
    * We ask that you use `get_float` so that you can handle dollars and cents, albeit sans dollar sign. In other words, if some customer is owed $9.75 (as in the case where a newspaper costs 25¢ but the customer pays with a $10 bill), assume that your program's input will be `9.75` and not `$9.75` or `975`. However, if some customer is owed $9 exactly, assume that your program's input will be `9.00` or just `9` but, again, not `$9` or `900`. Of course, by nature of floating-point values, your program will likely work with inputs like `9.0` and `9.000` as well; you need not worry about checking whether the user's input is "formatted" like money should be.
* You need not try to check whether a user's input is too large to fit in a `float`. Using `get_float` alone will ensure that the user's input is indeed a floating-point (or integral) value but not that it is non-negative.
* If the user fails to provide a non-negative value, your program should re-prompt the user for a valid amount again and again until the user complies.
* So that we can automate some tests of your code, be sure that your program's last line of output is only the minimum number of coins possible: an integer followed by `\n`.
* Beware the inherent imprecision of floating-point values. Recall [`floats.c`](https://sandbox.cs50.io/575cd269-8b4e-4a01-bc9f-3de38614b43e) from class, wherein, if `x` is `2`, and `y` is `10`, `x / y` is not precisely two tenths! And so, before making change, you'll probably want to convert the user's inputted dollars to cents (i.e., from a `float` to an `int`) to avoid tiny errors that might otherwise add up! 
* Take care to round your cents to the nearest penny, as with `round`, which is declared in `math.h`. For instance, if `dollars` is a `float` with the user's input (e.g., `0.20`), then code like

  ```
  int coins = round(dollars * 100);
  ```

  will safely convert `0.20` (or even `0.200000002980232238769531250`) to `20`.

Your program should behave per the examples below.

```
$ ./cash
Change owed: 0.41
4
```

```
$ ./cash
Change owed: -0.41
Change owed: foo
Change owed: 0.41
4
```

{% spoiler "Hints" %}

{% video https://www.youtube.com/watch?v=2QZSsaSfB3A %}

{% endspoiler %}

### Staff's Solution

To try out the staff's implementation of this problem, execute

```
./cash
```

within [this sandbox](https://sandbox.cs50.io/0551a578-189e-4989-9e89-99e41a4f2c6d).

### How to Test Your Code

Does your code work as prescribed when you input

* `-1.00` (or other negative numbers)?
* `0.00`?
* `0.01` (or other positive numbers)?
* letters or words?
* no input at all, when you only hit Enter?

{% next %}

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2018/fall/cash
```
