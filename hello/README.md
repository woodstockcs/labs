# Hello

{% video https://www.youtube.com/watch?v=DmE9lCvrxgU %}

{% next %}

## Listing Files

Hello, world! At right, in the *text editor*, is the very first program we will complete in C, in a file called `hello.c`. 

Click the folder icon, and you'll see that `hello.c` is the only file that's present at the moment. Per the mention of `/root/sandbox` below that icon, `hello.c` happens to be in a folder (otherwise known as a *directory*) called `sandbox`, which itself is in another folder called `root`. Click the folder icon again to hide all that.

Next, in the *terminal window* at right, immediately to the right of the dollar sign (`$`), otherwise known as a *prompt*, type precisely the below (in lowercase), then hit Enter:

```
ls
```

You should see just `hello.c`? That's because you've just listed the files in that same folder, this time using a command-line interface (CLI), using just your keyboard, rather than the graphical user interface (GUI) represented by that folder icon. In particular, you *executed* (i.e., ran) a command called `ls`, which is shorthand for "list." (It's such a frequently used command that its authors called it just `ls` to save keystrokes.) Make sense?

Here on out, to execute (i.e., run) a command means to type it into a terminal window and then hit Enter. Commands are "case-sensitive," so be sure not to type in uppercase when you mean lowercase or vice versa.

{% next %}

Shall we have you write your first program? In the file named hello.c, write your first program by typing precisely these lines into the file on the line in between the curly brackets:

```c
printf("hello, world\n");
```

so that your file looks like:

```c
#include <stdio.h>

int main(void)
{
    printf("hello, world\n");
}
```

{% next %}

## Compiling Programs

Now, before we can execute the program at right, recall that we must *compile* it with a *compiler*, translating it from *source code* into *machine code* (i.e., zeroes and ones). Execute the command below to do just that:

```
make hello
```

And then execute this one again:

```
ls
```

This time, you should see not only `hello.c` but `hello` listed as well? (You can see the same graphically if you click that folder icon again.) That's because `make` has translated the source code in `hello.c` into machine code in `hello`, which happens to be the zeros and ones that the computer understands.

Now run the program by executing the below.

```
./hello
```

Hello, world, indeed!

{% next "Ready to Submit?" %}

## How to Submit

Type the line below into your terminal to submit. No more having to make branches in and uploading your files into github! Juse execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2019/ap/hello
```

