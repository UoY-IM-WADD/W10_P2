# Week 10, Practical 2

## Stage 2 - Library Tutorials

Contents:
- [How to Use Font Awesome Icons](#how-to-use-font-awesome-icons)
- [p5js Basics](#p5js-basics)
- [Create a Webcam Background With TensorFlow](#create-a-webcam-background-with-tensorflow)

## How to Use Font Awesome Icons
Font Awesome provides high quality free icons that can be used in your HTML and styled with CSS (colour, size). They are very useful for menus, action buttons (e.g. edit, delete) and can also be used as basic sprites. Depending on how you install it, using Font Awesome doesn’t require JS.

### Setup
The following instructions are an amalgamation of the relevant bits and pieces from [the Font Awesome website](https://fontawesome.com/download). The website provides other options but most of them risk breaking the constraints of assessment 2. 

1.	Make a copy of the template folder, which you can find in the practical materials or in this repo, or create a new basic HTML page and linked CSS and JS files.
2.	Go to the [Font Awesome download page](https://fontawesome.com/download) and look for the box titled "6.3.0 for the web". Click the "Free for Web" button to download a zip of all the files you’ll need plus a bunch that won’t be needed.
3.	Extract the zip. Copy the webfonts and css folders (folders and contents) into the folder with your index.html file. You can move the copied folders into a nested folder if you prefer. Just make sure that webfonts and css folders are in the same folder. 
4.	Open the css folder and delete everything except all.css as it won’t be needed.
5.	Link all.css to your HTML page in the same way as your own css file. If you want to customise the icon appearance (colour, size) link all.css before your own stylesheet.

### Using a Font Awesome icon in HTML
1.	Go to [the icon reference](https://fontawesome.com/icons) and find an icon you like. You can search by keyword or explore the categories on that page.
2.	Although there are lots of free icons, some are Pro only (i.e. paid). On the icon search result page, there is an option to show only free icons. Identify a free icon that you like and click on it to get usage instructions.
3.	Clicking on an icon opens a modal window. In the top right, you will see some HTML code (an `<i>` element with classes). Copy this code and paste it into your index.html file. You will see the icon displayed when you load your HTML file using Live Preview.

### Styling a Font Awesome icon
The classes supplied by Font Awesome are required to display the icon. Icons will usually have two classes. Do not delete or rename either of these classes. Do not attempt to edit all.css either.

To style a Font Awesome icon add your own CSS in your own stylesheet. You can add your own custom classes to a Font Awesome icon by adding the class name to the end of the class list on the `<i>` element. You can also give icons an id and apply style rules to all icons by selecting the `i` tag in your CSS.

The icon is rendered as a text element, so you can change colour by using the `color` property as you would for text. You can also change the size using the `font-size` property. Other properties you can change include `margin`, `padding`, and `position`.

Icons can be used anywhere you can use a span element: inside paragraphs, headings, links, list items, buttons, and more.

## p5js Basics
p5js is the JavaScript version of Processing.

### Setup
1.	Make a copy of the templates folder in the practical materials or create a new basic HTML page and linked CSS and JS files.
2.	Go to [https://p5js.org/download/](https://p5js.org/download/), scroll down to the "Single Files" section and look for the CDN button.
3.	Click the CDN button. This will take you to a new page. Under the Version dropdown menu, you will see several URLs. You want the first one, which ends in min.js. Click the icon that looks a like an empty HTML element: `</>` . This will add to your clipboard a complete `<script>` element with the `src` already populated. Paste this into your HTML file at the end of `<body>` but above the `<script>` element that links your own JS file.

### Create a basic sketch
The following steps are the same as the official [Getting Started tutorial](https://p5js.org/get-started/) but they have been adapted for use in VS Code rather than the p5js web editor.

Put the following code into your main.js file:
```Javascript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
}
```
*Important note: p5js does not seem to recognise arrow functions. Write all functions using traditional function syntax.*

Notice that p5js has `setup()` and `draw()` functions just like Processing. These functions work in exactly the same way. `setup()` is run once when the page loads and should be used to set up the canvas and do any other initialisation that’s needed; `draw()` is called once per frame.

Most built-in functions and system variables are the same as in p5js as they are in Processing but there are a few exceptions. One exception is how the canvas is created. In Processing, you call `size()` and pass it a width and height. In p5js, you call `createCanvas()` instead. It also expects a width and height.

Run index.html using Live Preview if you haven’t done so already. Use Chrome Developer Tools to figure out how p5js draws on the webpage—look for a specific element that’s not in your HTML file but appears in the Inspect pane in Chrome. 

Use your knowledge of Processing to complete each of the steps below. The code is exactly the same in p5js as in Processing unless otherwise noted. Check the sketch output after each bullet point.
- The sketch background is greyscale. Make it an RGB colour instead.
- Draw a circle at 50, 50 and give it a radius of 80 pixels. 
- Give the circle a different fill colour when the mouse is pressed. In Processing, you could use the `mousePressed` system variable. In p5js, the equivalent variable is called `mouseIsPressed`.
- Modify your code so that the circle follows the mouse.

### Using HTML input controls with your p5js sketch
Because p5js runs in the browser, you can use standard HTML input elements to add more user control to your sketch.

Start by adding a standard HTML button that will appear above the sketch, rather than inside it. In your HTML file, add an HTML button input and give it an `id` and a value. The button will be used to change the background colour of your sketch. If you check the output, you should see that the button appears above the sketch.

In main.js, look at how and where the background colour is set. It is called with a hard-coded colour value every time `draw()` is called. As with regular Processing, if you want to be able to change the colour in response to user input, you will need a global variable to store the current colour and pass that variable to `background()` instead of the hard-coded value. In Processing, you could call some built-in functions like `color()` where global variables are initialised (outside `setup()`). In p5js, however, these functions can only be called inside `setup()` or after `setup()` has run. To create and use a variable to set the background colour, do the following:

- Declare the variable at the top of main.js. Don’t give it a value.

```javascript
let bgColour;
```
- Anywhere in `setup()`, assign the variable a colour of your choosing using the `color()` function. E.g.:
```javascript
bgColour = color(255, 255, 0);
```
- Replace the hard-coded numbers in `background()` with the variable name:
```javascript
background(bgColour); 
```
Check that everything works before moving on. 

Next, add an event listener to your button that will give your background colour variable a new value when the button is clicked. You can call the p5js `color()` function inside your event handler. You can also use an anonymous function (traditional or arrow) to implement the event handler as you would in vanilla JS.

Hopefully this tutorial will help you get started with p5js. There are lots of things you can do with this library. Here are some suggestions if you would like to go further:
- Explore the DOM section of the p5js reference. It provides its own syntax for adding input elements and capturing events directly on the canvas.
- p5js always adds the canvas to the end of the `<body>`, after anything else that’s rendered. Take a look at [this page](https://github.com/processing/p5.js/wiki/Positioning-your-canvas) for guidance on how to position the canvas elsewhere.
- Try translating some of your Processing work (or lecture / practical sample code) from PDM or CT into p5js. For example, the Pong game from PDM practical 3 would be a good option. Keep in mind that while a lot of the syntax is similar between the two versions there are some differences—keep the p5js reference open as you work.

## Create a Webcam Background With TensorFlow
