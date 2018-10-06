# Pennies

{% video https://www.youtube.com/watch?v=cqiRNWH4OfU %}

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

If ever given the choice between $10,000,000 or a month’s worth of pennies, whereby you receive a penny the first day, two pennies the second, four pennies the third, and so forth…​ take the pennies.

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

Of course, if you store the user’s amount due in an int (which is only 32 bits), the total will be bounded by (2<sup>31</sup> - 1) pennies. (Why 2<sup>31</sup> and not 2<sup>32</sup>? And why 1 less than 2<sup>31</sup>?) Best, then, to store your total in a long long, so that the user benefits from 64 bits. (Don’t worry if users' totals overflow 64 bits and even go negative; consider it punishment for greed!)

Do take care to format the user’s total as dollars and cents (to just 2 decimal places), prefixed with a dollar sign, just as we did in the output above. You do not need to insert commas after every 3 digits to the left of the decimal, as you might normally do.

So that we can automate some tests of your code, we ask that your program’s last line of output be the amount owed to a user, followed by \n. The rest of your program’s personality we leave entirely to you!


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
submit50 cs50/2018/ap/pennies
```

To make sure you get 5/5 for style, you may want to execute style50 firt.

```
style50 pennies.c
```


