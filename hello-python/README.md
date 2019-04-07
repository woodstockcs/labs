# Hello (in Python!)

{% video https://www.youtube.com/embed/5ueXMnDE-y8 %}

{% next %}

## Hello, Python!

If you've taken CS50 Intro this year, you've already created Hello in C. If you haven't, no worries, just ignore the C code referenced here. In either case, will be writing what might be your first Python program!

{% next %}

You will write your hello program in the file to the right, hello.py. Since Python is an interpreted language, there is no need to compile! To run your code, simply type in 

```
python hello.py
```
in the lower terminal window.

{% next "Ready for the next step?" %}

Now that was almost too easy!

Let's make this a bit more interesting now by adding user input and saying hello, followed by whatever name you choose to input.

No matter how you execute this program right now, it only ever prints hello, world.

There will be a few important differences to create this program. You will need to get user input, and CS50 makes some easy to use functions to help you with this. To access these user input functions you will have to import them from a special cs50 module. In this case you will want to import a name, which is considered a `string` so you will want to import get_string.

```python
from cs50 import get_string
```

A string in computer science essentially refers to a collection of characters—​a word, a sentence, or a phrase. Because when you ask the user for their name, you would use get_string to collect their input and to store it in a variable whose data type is string.

What else will change, though? That last line of code. You'll need to add %s in there, and the variable name. Why is that the case?

Essentially, %s is what’s known as a placeholder for a variable. At the time the program is compiled, we don’t know exactly what will be printed out (unlike the original program which will always print out hello, world\n), but we do expect that the program will print hello, followed by whatever the user typed. %s is how we indicate to printf that a string will be printed there.

What string will we print? Well, that’d be name! After we specify what we want printf to print, leaving as many placeholders as necessary, we specify what variables those placeholders refer to in order from left to right, separated by commas. We only have one placeholder in our modified program, a single %s, and so the variable that we’re telling printf to print in place of that %s is whatever the user typed at the prompt. For example:


