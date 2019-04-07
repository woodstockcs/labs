# Water

{% video https://youtu.be/Vpa3s-tnrMA %}

{% next %}

## Background

Suffice it to say that the longer you shower, the more water you use. But just how much? Even if you have a "low-flow" showerhead, odds are your shower spits out 1.5 gallons of water per minute. A gallon, meanwhile, is 128 ounces, and so that shower spits out 1.5 × 128 = 192 ounces of water per minute. A typical bottle of water (that you might have for a drink, not a shower), meanwhile, might be 16 ounces. So taking a 1-minute shower is akin to using 192 ÷ 16 = 12 bottles of water. Taking (more realistically, perhaps!) a 10-minute shower, then, is like using 120 bottles of water. Deer Park, that’s a lot of water! Of course, bottled water itself is wasteful; best to use reusable containers when you can. But it does put into perspective what’s being spent in a shower!

{% next %}

In this lab, you will write a program that reports a user's water usage, converting the number of minutes spent in the shower, to bottles of drinking water.

For example, if the user inputs 1 minute, the output should be 12 bottles as below. If the minutes is input as 10, then the output should be 120 bottles.

```
python water.py
Minutes: 1
Bottles: 12

python water.py
Minutes: 10
Bottles: 120

```

{% next %}

## Specification

Write, in a file called water.py, a program that prompts the user for the length of his or her shower in minutes (as an integer) and then prints the equivalent number of bottles of water (as an integer)

For simplicity, you may assume that the user will input a positive integer, so no need for error-checking (or any loops) this time! And no need to worry about overflow!

Since we want the user input to be an integer, we can use the CS50 function get_int. This works in a very similar way as get_string did in your last problem, but it will only accept integers as input, and if you input anything else, it will ask you to retry.

Remember, you'll have to import get_int from the CS50 Module first.

{% spoiler "Hint" %}
At the top of your program, you should have the following code:

```python
from cs50 import get_int
```
{% endspoiler %}

Now go ahead and asign the output from get_int to a variable to store the number of minutes.

{% spoiler "Hint" %}
```python
n = get_int("Minutes: )
```
{% endspoiler %}

Once we get the user input, we'll want to calculate the number of bottles used. This may be very obvious to you at first, but it's a good idea to get into the habit of detecting patterns to write algorithms to solve problems. We're told, per the spec, that one minute is the equivalent of 12 bottles of water. So then two minutes would be equivalent to 24.

#### Per the spec
* 1 min = 12 bottles of water
* 2 min = 24 bottles of water
* ...
* 5 min = 60 bottles of water

* n min = ?? bottles of water

So for n minutes, how many bottles of water would be used in terms of n.

{% next %}

In Python, you have access to standard artithmetic operations such as:
* add:      num1 + num2
* subtract: num1 - num2
* multiply: num1 * num2
* divide:   num1 / num2

Now we'll leave it to you to figure out how to express the equivalent number of bottles in Python.



