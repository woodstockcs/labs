# Fahrenheit



{% next %}

## Turning Up The Heat

In the past, if you wanted to know what the outdoor temperature was, you had to look around for one of these, which might have been mounted outside at your house.

Prior to that, if you wanted to know what the temperature was outside, you just stood outside, but we digress. Nowadays, it’s a fairly trivial exercise to pull open a weather app on your phone or visit a weather-reporting website to get the current temperature and the five-day forecast. No need to mess around with one of the above circular dials or its tube-of-mercury cousin.

Depending on where you live in the world, your country uses one of two major temperature scales. If you live in the United States (and don’t spend most of your day working in a science lab), it’s likely that you’re familiar with the Fahrenheit scale, and so if you hear that it’s 30° outside you’re probably putting on a heavy coat and warm pants and bracing yourself for the possibility of snow, because that means it’s quite cold, given that the freezing point of water is 32°. On the other hand, it’s not until the temperature hits 212° that water boils.

{% next %}

In practically every other country of the world (or if you live in the United States and do in fact spend most of your day working in a science lab), you’re probably most familiar with the Celsius or centigrade scale. In that case, if you hear that it’s 30° outside you’re probably going to rummage through your closet for a swimsuit and put on some sunblock, because it’s a beautiful beach day. On the Celsius scale, 0° is the freezing point of water, and 100° is the boiling point.

We acknowledge that with most apps that tell you the weather, it’s fairly simple to press that switch that switches the temperature display from Fahrenheit to Celsius (or vice versa), but before that process was automated for us, one either had to memorize some of the more common conversion points or had to use a mathematical formula to convert from one scale to another, which is important if you plan on traveling internationally.

For this problem, we’re going to focus on converting in just one direction: from Celsius to Fahrenheit. As it happens, the formula for this conversion isn’t terribly complex. (Phew!) One simply takes the current temperature in degrees Celsius (°C), multiplies it by 9, divides by 5, and then adds 32. The result is the equivalent temperature in degrees Fahrenheit (°F). Not bad, right? For the more visually inclined, this translates to this formula:

```
F = ((C * 9) / 5) + 32
```

Let’s do a quick test to make sure things work as expected. Worldwide, the commonly accepted value for normal human body temperature is 37°C. If we plug "37" into that formula where °C goes and do the math (37 multiplied by 9 is 333, 333 divided by 5 is 66.6, 66.6 + 32 is 98.6) we get 98.6°F which is what folks in the United States know as normal human body temperature. So that checks out. Similarly if we plug in 0°C (the freezing point of water) into that formula does it convert to 32°F, and 100°C (the boiling point of water) is apparently equivalent to 212°F. Seems like things are going well.

{% next %}

So your job is to write a program that converts a temperature in Celsius to Fahrenheit, as per the sample output below, wherein underlined text represents some user’s input.

```
$ ./fahrenheit
C: 100
F: 212.0
```

{% next %}

## Pseudocode

First, write in `pseudocode.txt` at right some pseudocode that implements this program, even if not (yet!) sure how to write it in code. 

Odds are your pseudocode will use (or imply using!) one or more functions, operators, and variables.

{% spoiler %}

<p>
  There's more than one way to do this, so here's just one!
</p>

<ol>
  <li>Prompt for degrees Celsius and save this in a variable</li>
  <li>Use this value to calculate degrees Fahrenheit and save in another variable</li>
  <li>Print out the result</li>
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
