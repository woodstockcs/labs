# DVD Animation

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

!{Canvas](http://intro.cs50nestm.net/wp-content/uploads/2019/03/canvas.png)


## How to View Your Web Page

Type http-server in the terminal and click on the link. You will open a new browser window with your web page!

## To get more help with HTML and CSS

* [HTML](https://www.w3schools.com/html/)

* [CSS](https://www.w3schools.com/css/)

## How to Submit

To ensure that your page is well formed, you can use the [W3Schools HTML Validator service](https://validator.w3.org/#validate_by_input), copying and pasting your HTML directly into the provided text box. 

You may then submit by typing in at the command line:

submit50 cs50/2018/ap/unit5


