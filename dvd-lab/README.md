# DVD Animation with p5.js

Ths goal of this lab is to create a DVD animation as seen in this episode of The Office.

{% video https://www.youtube.com/watch?v=QOtuX0jL85Y&t=3s %}

But first we need to become familiar with drawing with p5.js.

{% next %}

## Getting Ready

For this project you will p5.js, a JavaScript library that has a full set of drawing and animation tools. Note that in this lab there are separate HTML and JavaScript files. The HTML does nothing more than import the required p5 libararies as well as the JavaScript files you will create so that you can run your animations. You do not need to change the HTML at this point, all your programming will be done in your sketch.js files.

{% next %}

A typical p5.js sketch starts with a p5 function, setup(). Instructions in the setup() function are run once when the program starts. It's used to define initial environment properties such as screen size and background color and to load media such as images and fonts as the program starts. 

```javascript
function setup() {
  createCanvas(600, 400)
}
```

This will create your "canvas" as a rectangular area on your web page, with a width of 600 and a height of 400.

Another p5 function you will be using is draw(). The draw() function runs immediately after setup(), and it runs repeatedly, allowing for moving animation.  A single execution of the draw() function from top to bottom represents a single “frame” of an animation.  The number of times draw() executes in each second may be controlled with the frameRate() function. The default frame rate is 60 frames per second. There can only be one draw() function for each sketch. 

```javascript
function draw() {
  // put your code for drawing here
}
```
{% next %}

Here is a representation of pixels on a 400 x 400 canvas. Note that the y-axis is flipped compared to yuor math class!

![Canvas](http://intro.cs50nestm.net/wp-content/uploads/2019/03/canvas.png)

A few of the p5.js functions you will find useful include:
1. `fill(color)` which sets the color that all subsequent shapes are filled with. For example, `fill(50)` fills shapes with grayscale, while `fill(204, 102, 0)` fills shapes with orange. https://p5js.org/reference/#/p5/fill
1. `ellipse(x, y, width, height)` draws an ellipse, specifying the coordinates (x,y) of the center, width, and height.  
1. `rect(x, y, width, height)` draws a rectangle, specifying the coordinates (x,y) of the top left corner, width, and height. Check out `rectMode()` here: https://p5js.org/reference/#/p5/rectMode
1. `triangle(x1, y1, x2, y2, x3, y3)` draws a triangle, specifying the coordinates of three vertices: (x1,y1), (x2,y2), and (x3,y3)

More functions and details on these functions can be found at https://p5js.org/reference.

{% next %}

## Warmup #1

1. Open up `sketch1.js` and type in the following:

```javascript
function setup() {
  create Canvas(400, 400)
  background(0, 0, 255)
}

function draw() {
  if (mousePressed) {
    fill(255, 0, 0)
    ellipse(mouseX, mouseY, 40, 40)    
  }
}
```
1. To see what this code does, open http-server and open the file page1.html. Make sure you press and move the mouse over the canvas.
1. Once you have your first program working, make each change described below.  After each individual change,  press and move the mouse over the canvas to see what happens.
1. On Line 2, change createCanvas(400,400) to createCanvas(600, 400)
1. On Line 3, change background(0, 0, 255) to background(255, 0, 255)
1. On Line 8, change fill(255, 0, 0) to fill(0, 255, 0)
1. On Line 9, change noStroke() to stroke(0, 0, 255)
1. Change Line 10 to be ellipse(mouseX, 0, 40, 40)
1. Change Line 10 to be ellipse(mouseX, mouseY, 100, 50)
1. Remove the if(mousePressed){ from Line 7 and also remove its ending } on Line 11.
C1. ut the background command from Line 3 and paste it onto Line 7, so that it is in between function draw(){ and fill(0, 255, 0).

{% next %}

## Warmup #2

You’ll be making this “spaceship” below.

![Spaceship](http://intro.cs50nestm.net/wp-content/uploads/2019/03/Screen-Shot-2019-03-25-at-6.48.21-AM.png)

1. (no coding)  Assume that the center  of the circle is given by(x,y)and the width of the square is 50 pixels.  Figure out the coordinates of the vertices of the triangle relative to x and y.  
2. Open the file sketch2.js and code it. Use the code below as starter code and complete the missing pieces:

```javascript
let x = 200
let y = 250

function setup() {
  createCanvas(400, 400)
  rectMode(CENTER)
}

function draw() {
  // TODO 
}
```
3. Once you have a working spaceship: in the draw() function add the command `y = y – 1`;

## DVD Logo Challenge

1. Start by creating a rectangle and have it bounce off the sides of the screen.
1. Have the rectangle change colors when bouncing off the side of a screen (this can be random, or a predetermined set of colors)
1. Have rectangle play a “boing” sound when it bounces off the side of a wall (you might want to look at p5-sound to achieve this)
1. When the rectangle hits a corner of the screen, have it stop the animation and display some sort of celebratory gif or message on the screen.
1. Load the DVD logo into your sketch and replace the rectangle with this logo: https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ8j2ZvogClZN_eBG7qKeZUCcHweqjjsulAsOGOzKvhkQ2iEEzF

## How to Submit

Submission information to come soon!


