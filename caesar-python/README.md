# Caesar (Python)

{% video https://www.youtube.com/watch?v=5I7QqTTolHE %}

{% next %}

## Et tu?

Supposedly, Caesar (yes, that Caesar) used to "encrypt" (i.e., conceal in a reversible way) confidential messages by shifting each letter therein by some number of places. For instance, he might write A as B, B as C, C as D, ..., and, wrapping around alphabetically, Z as A. And so, to say HELLO to someone, Caesar might write IFMMP. Upon receiving such messages from Caesar, recipients would have to "decrypt" them by shifting letters in the opposite direction by the same number of places.

The secrecy of this "cryptosystem" relied on only Caesar and the recipients knowing a secret, the number of places by which Caesar had shifted his letters (e.g., 1). Not particularly secure by modern standards, but, hey, if you're perhaps the first in the world to do it, pretty secure!

Unencrypted text is generally called _plaintext_. Encrypted text is generally called _ciphertext_. And the secret used is called a _key_.

To be clear, then, here's how encrypting `HELLO` with a key of 1 yields `IFMMP`:

| plaintext    | H | E | L | L | O |
|--------------|---|---|---|---|---|
| + key        | 1 | 1 | 1 | 1 | 1 |
| = ciphertext | I | F | M | M | P |

More formally, Caesar's algorithm (i.e., cipher) encrypts messages by "rotating" each letter by _k_ positions. More formally, if _p_ is some plaintext (i.e., an unencrypted message), _p<sub>i</sub>_ is the _i<sup>th</sup>_ character in _p_, and _k_ is a secret key (i.e., a non-negative integer), then each letter, _c<sub>i</sub>_, in the ciphertext, _c_, is computed as

c<sub>i</sub> = (p<sub>i</sub> + k) % 26

wherein `% 26` here means "remainder when dividing by 26." This formula perhaps makes the cipher seem more complicated than it is, but it's really just a concise way of expressing the algorithm precisely. Indeed, for the sake of discussion, think of A (or a) as 0, B (or b) as 1, ..., H (or h) as 7, I (or i) as 8, ..., and Z (or z) as 25. Suppose that Caesar just wants to say Hi to someone confidentially using, this time, a key, _k_, of 3. And so his plaintext, _p_, is Hi, in which case his plaintext's first character, _p<sub>0</sub>_, is H (aka 7), and his plaintext's second character, _p<sub>1</sub>_, is i (aka 8). His ciphertext's first character, _c<sub>0</sub>_, is thus K, and his ciphertext's second character, _c<sub>1</sub>_, is thus L. Can you see why?

Take a look at [this rotational model](http://cipher.cs50nestm.net){:target="_blank"} 

Let's write a program called `caesar` that enables you to encrypt messages using Caesar's cipher. At the time the user executes the program, they should decide, by providing a command-line argument, on what the key should be in the secret message they'll provide at runtime. We shouldn't necessarily assume that the user's key is going to be a number; though you may assume that, if it is a number, it will be a positive integer.

Here are a few examples of how the program might work. For example, if the user inputs a key of `1` and a plaintext of `HELLO`:

```
$ python caesar.py 1
plaintext:  HELLO
ciphertext: IFMMP
```

Here's how the program might work if the user provides a key of `13` and a plaintext of `hello, world`:

```
$ python caesar.py 13
plaintext:  hello, world
ciphertext: uryyb, jbeyq
```

Notice that neither the comma nor the space were "shifted" by the cipher. Only rotate alphabetical characters!

How about one more? Here's how the program might work if the user provides a key of `13` again, with a more complex plaintext:

```
$ python caesar.py 13
plaintext:  be sure to drink your Ovaltine
ciphertext: or fher gb qevax lbhe Binygvar
```

Notice that the case of the original message has been preserved. Lowercase letters remain lowercase, and uppercase letters remain uppercase.

And what if a user doesn't cooperate?

```
$ python caesar.py
Usage: python caesar.py k
```

Or really doesn't cooperate?

```
$ python caesar.py 1 2 3 4 5
Usage: python caesar.py k
```

Be sure to watch the walkthrough above for more detail on how to implement.

{% next %}

## Specification

Design and implement a program, caesar, that encrypts messages using Caesar’s cipher.

* Implement your program in a file called caesar.py (if it doesn’t already exist, create it now!).

* Your program must accept a single command-line argument, a non-negative integer. Let’s call it k for the sake of discussion.

{% spoiler "Hints" %}

Recall that argv is a list of strings representing the command line arguments. Recall that we can use len(argv) in order to figure out how many strings exist in that list; this is the equivalent idea to argc, from C.

And so you can access k with code like

```python
k = argv[1]
```

assuming it’s actually there! And assuming you’ve imported argv, as by:

```python
from sys import argv
```

{% endspoiler %}

* If your program is executed without any command-line arguments or with more than one command-line argument, your program should print an error message of your choice (with print) and exit immediately with a status code of 1.

* You can assume that, if a user does provide a command-line argument, it will be a non-negative integer (e.g., 1). No need to check that it’s indeed numeric.

* Do not assume that k will be less than or equal to 26. Your program should work for all non-negative integral values of k. But, even if k is greater than 26, alphabetical characters in your program’s input should remain alphabetical characters in your program’s output. For instance, if k is 27, A should not become [ even though [ is 27 positions away from A in ASCII, per asciichart.com; A should become B, since B is 27 positions away from A, provided you wrap around from Z to A.

{% spoiler "Hints" %}

Note that in Python, you can iterate over the characters in a string, printing each one at a time, with code like the below:

```python
for c in p:
    print(c, end="")
```

That `end=""` line just overrides Python’s default behavior when printing which, unlike C, tacks on a newline by default!

You may also wish to have a look at Python’s `ord()` and `chr()` functions!

{% endspoiler %}

* Your program must output plaintext: (without a newline) and then prompt the user for a string of plaintext (using get_string).

* Your program must output ciphertext: (without a newline) followed by the plaintext’s corresponding ciphertext, with each alphabetical character in the plaintext "rotated" by k positions; non-alphabetical characters should be outputted unchanged.

* Your program must preserve case: capitalized letters, though rotated, must remain capitalized letters; lowercase letters, though rotated, must remain lowercase letters.

* After outputting ciphertext, you should print a newline.

{% next %}


## Your Turn

Now it's time to tie everything together! And be sure to preserve case! Uppercase letters should stay uppercase, lowercase letters should stay lowercase, and characters that aren't alphabetical should remain unchanged.

{% spoiler "Hints" %}

* Best to use the modulo (i.e., remainder) operator, `%`, to handle wraparound from Z to A! But how?
* Recall that ASCII maps all printable characters to numbers.
* Recall that the ASCII value of `A` is 65. The ASCII value of `a`, meanwhile, is 97.
* If you're not seeing any output at all when you call `print`, odds are it's because you're printing characters outside of the valid ASCII range from 0 to 127. 

{% endspoiler %}

## Now be sure to test your code

Try out different types of plaintext to encrypt into ciphertext. Make sure you include lower and upper case letter, as well as non-alphabetic characters. Once your outputs match the examples above you have succeeded! Congratulations!
