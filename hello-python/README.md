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

Let's change this code to interact with the user like this, when executed.

```
python hello.py
Name: Alice
hello, Alice
```

There will be a few important differences to create this program. You will need to get user input, and CS50 makes some easy to use functions to help you with this. To access these user input functions you will have to import them from a special cs50 module. In this case you will want to import a name, which is considered a `string` so you will want to import get_string.

```python
from cs50 import get_string
```

A string in computer science essentially refers to a collection of characters—​a word, a sentence, or a phrase. Because when you ask the user for their name, you would use get_string to collect their input and to store it in a variable whose data type is string.

We can use get_string, and assign the input to a variable, such as `name` like this:

```python
name = get_string("Name: ")
```

Now the user input (hopefully a name!), will be stored in the variable `name`.

What else will change, though? Well, we need to change the print statement to include the name! 

In Python, we can pass in multiple variables into the print function, which will print them for us on the same line, separated by a space automatically.

So if the variable `name` contains the string, `Alice`, I can print out `hello, Alice` like this:

```python
print("hello,", name)
```

And be sure to execute your program, testing it a few times with different inputs, with:

```
python hello.py
```

Congratulations! You've completed your first Python program!

{% next %}
