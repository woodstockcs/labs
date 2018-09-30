# Hello, Tahmidul

{% video https://www.youtube.com/watch?v=eunVUd6E-Bs %}

## Enhancing our first program

To the right you should see the first program you just submitted, hello. Let's make this a bit more interesting now by adding user input and saying hello, followed by whatever name you choose to input. David is the first name of Havard's CS50 Professor, David Malan.

No matter how you compile or execute this program right now, it only ever prints `hello, world`.

## Getting User Input

Modify this program in such a way that it first prompts the user for their name and then prints `hello, so-and-so`, where `so-and-so` is their actual name.

As before, be sure to compile your program with:

```
make hello
```

And be sure to execute your program, testing it a few times with different inputs, with:

```
./hello
```

### Staff's Solution

To try out the staff's implementation of this problem, execute

<pre>
./hello
</pre>

within <a href="https://sandbox.cs50.io/0c8ebcaa-ca6e-45fa-bff2-043e5e6d83ec">this sandbox</a>.

### Hints

#### Don't recall how to prompt the user for their name?

Recall that you can use `get_string` as follows, storing its *return value* in a variable called `name` of type `string`.

```c
string name = get_string("What is your name?\n");
```

#### Don't recall how to format a string?

Don't recall how to join (i.e., concatenate) the user's name with a greeting? Recall that you can use `printf` not only to print but to format a string (hence, the `f` in `printf`), a la the below, wherein `name` is a `string`.

```c
printf("hello, %s\n", name);
```

#### Use of undeclared identifier?

Seeing the below, perhaps atop other errors?

```
error: use of undeclared identifier 'string'; did you mean 'stdin'?
```

Recall that, to use `get_string`, you need to include `cs50.h` (in which `get_string` is *declared*) atop a file, as with:

```c
#include <cs50.h>
```

{% next %}

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2018/fall/hello
```
