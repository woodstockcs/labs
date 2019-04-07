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

Write, in a file called water.py, a program that prompts the user for the length of his or her shower in minutes (as a positive integer) and then prints the equivalent number of bottles of water (as an integer)

For simplicity, you may assume that the user will input a positive integer, so no need for error-checking (or any loops) this time! And no need to worry about overflow!

To get 

{% spoiler "Hint" %}

```python
name = get_string("Name: ")
```
{% endspoiler %}

Now the user input (hopefully a name!), will be stored in the variable `name`.

What else will change, though? Well, we need to change the print statement to include the name! 

In Python, we can pass in multiple variables into the print function, which will print them for us on the same line, separated by a space automatically.

{% spoiler "Hint" %}

If the variable `name` contains the string, `Alice`, I can print out `hello, Alice` like this:

```python
print("hello,", name)
```

{% endspoiler %}

{% next %}

When you are done be sure to execute your program, testing it a few times with different inputs, with:

```
python hello.py
```

Congratulations! You've completed your first Python program!


