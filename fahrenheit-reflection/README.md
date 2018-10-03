# Fahrenheit

{% video https://www.youtube.com/watch?v=C-5-22ZvW40 %}

{% next %}

## Turning Up The Heat

In the past, if you wanted to know what the outdoor temperature was, you had to look around for one of these, which might have been mounted outside at your house.

## Pseudocode

First, write in `pseudocode.txt` at right some pseudocode that implements this program, even if not (yet!) sure how to write it in code. There's no one right way to write pseudocode, but short English sentences suffice. Recall how we wrote pseudocode for [finding Mike Smith](https://cdn.cs50.net/2018/fall/lectures/0/lecture0.pdf). Odds are your pseudocode will use (or imply using!) one or more functions, conditions, Boolean expressions, loops, and/or variables.

{% spoiler %}

<p>
  There's more than one way to do this, so here's just one!
</p>

<ol>
  <li>Prompt user for height</li>
  <li>If height is less than 1 or greater than 8 (or not an integer at all), go back one step</li>
  <li>
    Iterate from 1 through height:
    <ol>
      <li>On iteration <em>i</em>, print <em>i</em> hashes and then a newline</li>
    </ol>
  </li>
</ol>

<p>
  It's okay to edit your own after seeing this pseudocode here, but don't simply copy/paste ours into your own!
</p>

{% endspoiler %}

{% next %}

## Prompting for Input

Whatever your pseudocode, let's first write only the C code that prompts (and re-prompts, as needed) the user for input. 

Specifically, modify `mario.c` at right in such a way that it prompts the user for the pyramid's height, storing their input in a variable, re-prompting the user again and again as needed if their input is not a positive integer between 1 and 8, inclusive. Then, simply print the value of that variable, thereby confirming (for yourself) that you've indeed stored the user's input successfully, a la the below.

```
$ ./mario
Height: -1
Height: 0
Height: 42
Height: 50
Height: 4
Stored: 4
```

{% spoiler "Hints" %}

<ul>
  <li>Recall that you can compile your program with <code>make</code>.</li>
  <li>Recall that you can print an <code>int</code> with <code>printf</code> using <code>%i</code>.</li>
  <li>Recall that you can get an integer from the user with <code>get_int</code>.</li>
  <li>Recall that <code>get_int</code> is declared in <code>cs50.h</code>.</li>
  <li>Recall that we prompted the user for a positive integer in class via <a href="https://sandbox.cs50.io/b56865fd-c861-425f-aad7-4adcf6831139"><code>positive.c</code></a>.</li>
</ul>

{% endspoiler %}

## Building the Opposite

Now that your program is (hopefully!) accepting input as prescribed, it's time for another step.

It turns out it's a bit easier to build a left-aligned pyramid than right-, a la the below.

```
#
##
###
####
#####
######
#######
########
```

So let's build a left-aligned pyramid first and then, once that's working, right-align it instead!

Modify `mario.c` at right such that it no longer simply prints the user's input but instead prints a left-aligned pyramid of that height.

{% spoiler "Hints" %}

<ul>
  <li>Keep in mind that a hash is just a character like any other, so you can print it with <code>printf</code>.</li>
  <li>Just as Scratch has a <a href="https://cdn.cs50.net/2018/fall/lectures/0/lecture0.pdf">Repeat</a> block, so does C have a <a href="https://cdn.cs50.net/2018/fall/lectures/1/lecture1.pdf"><code>for</code></a> loop, via which you can iterate some number times. Perhaps on each iteration, <em>i</em>, you could print that many hashes?</li>
  <li>
    You can actually "nest" loops, iterating with one variable (e.g., <code>i</code>) in the "outer" loop and another (e.g., <code>j</code>) in the "inner" loop. For instance, here's how you might print a square of height and width <code>n</code>, below. Of course, it's not a square that you want to print!
<pre>
for (int i = 0; i < n; i++)
{
    for (int j = 0; j < n; j++)
    {
        printf("#");
    }
    printf("\n");
}
</pre>
  </li>
</ul>

{% endspoiler %}

{% next %}

## Right-Aligning with Dots

Let's now right-align that pyramid by pushing its hashes to the right by prefixing them with dots (i.e., periods), a la the below.

```
.......#
......##
.....###
....####
...#####
..######
.#######
########
```

Modify `mario.c` in such a way that it does exactly that!

{% spoiler "Hint" %}

Notice how the number of dots needed on each line is the "opposite" of the number of that line's hashes. For a pyramid of height 8, like the above, the first line has but 1 hash and thus 7 dots. The bottom line, meanwhile, has 8 hashes and thus 0 dots. Via what formula (or arithmetic, really) could you print that many dots?

{% endspoiler %}

### How to Test Your Code

Does your code work as prescribed when you input

* `-1` (or other negative numbers)?
* `0`?
* `1` through `8`?
* `9` or other positive numbers?
* letters or words?
* no input at all, when you only hit Enter?

{% next %}

## Removing the Dots

All that remains now is a finishing flourish! Modify `mario.c` in such a way that it prints spaces instead of those dots!

{% spoiler "Hint" %}

A space is just a press of your space bar, just as a period is just a press of its key! Just remember that `printf` requires that you surround both with double quotes!

{% endspoiler %}

{% next %}

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2018/fall/mario/less
```
