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
TensorFlow.js is a Google machine learning library that allows you to embed some AI capabilities in your web applications. Taking full advantage of TensorFlow.js requires advanced technical skills and knowledge of machine learning fundamentals but this tutorial is intended to be approachable with just the JS covered in this module. 

Most video conferencing apps allow users to blur their background or replace it with an image. This is done using a computer vision technique called segmentation, which separates background from objects of interest in an image. In this tutorial, you will use body segmentation, where the object of interest is a human, to create an image background. If you don’t have a webcam, you can still do the setup and the body segmentation sections of the tutorial. A webcam is required for the final section.

### Setup
1.	Make a copy of the templates folder in the practical materials or create a new basic HTML page and linked CSS and JS files.
2.	Add TensorFlow.js to your HTML file by copying the `<script>` element found under "Usage via script tag" on [this page](https://www.tensorflow.org/js/tutorials/setup) and pasting it just above the `<script>` element that connects main.js.
3.	TensorFlow.js provides pre-trained models for a number of tasks. To use a pre-trained model, you need to import it alongside the library itself. For this tutorial, you will need two pre-trained models for body segmentation. Import these models by copying the following script tags into your HTML between the script tag from step 2 and the script tag linking main.js:
```html
<script src="https://cdn.jsdelivr.net/npm/@mediapipe/selfie_segmentation"></script>
<script src="https://cdn.jsdelivr.net/npm/@tensorflow-models/body-segmentation@1.0.1"> </script>
```
### Body segmentation
The following steps are based on [this TensorFlow.js example](https://github.com/tensorflow/tfjs-models/tree/master/body-segmentation) but they have been heavily customised.

**Complete the HTML page**
1.	Copy the images folder from the practical materials into the folder that contains your HTML.
2.	In your index.html file, add an image element above the scripts and give it the `id` "image". Use the image called "StockSnap_5TCGRN12WA.jpg" as the image source. You will eventually use the body segmentation model to separate the person in the foreground of the image from the wall in the background.
3.	Below the image but above the scripts, add a canvas element, give it the `id` "canvas" and set its width and height to match the image (800px by 533px). The segmented image will be displayed on the canvas later on. Open index.html in Chrome using Live Preview and check that you see the image in your browser. 
4.	Give the canvas a CSS border or background colour so that you can see it on the screen even when nothing is drawn on it.

**Create global variables in your JS file**
1.	In your JS file, create global variables to store the image element, the canvas, and its context. When getting the canvas context, you will need to pass a second argument that will improve performance when the webcam is used. Here is the code:

```javascript
const image = document.getElementById("image");
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d", {willReadFrequently: true});
```
2.	Create another variable that will store a reference to TensorFlow’s bodySegmentation model. Copy this code as is:
```javascript
const model = bodySegmentation.SupportedModels.MediaPipeSelfieSegmentation;
```
3.	Add the following variable, a JSON object that stores configuration information for the model, such as which specific model to use:
```javascript
const segmenterConfig = {
  runtime: 'mediapipe', 
  solutionPath: 'https://cdn.jsdelivr.net/npm/@mediapipe/selfie_segmentation',
  modelType: 'general'
}
```
**Segment the image**
Using a machine learning model for classification typically involves three stages:
1. Loading the classifier, which is essentially a file or data structure containing a lot of numerical data
2. Passing some new data to the classifier and waiting for it to respond with a prediction or label
3. Doing something with the classifier output.

As models are generally very large, stages 1 and 2 can be slow so they are usually carried out using *asynchronous* operations, similar to the asynchronous operations to fetch data from a web API.

You will now write functions to carry out each stage.
1. Outline a function called `setup` using your preferred syntax. It should not have any parameters. This function will load the classifier, which we'll refer to as the "segmenter".
2. Outline a function called `segment` using your preffered syntax. It should have one parameter called `segmenter`. This function will pass data to the classifier and wait for a response.
3. Call `setup()` at the bottom of your script file.
4. Add the following code inside your `setup` function:

```javascript
bodySegmentation.createSegmenter(model, segmenterConfig)
                .then(segmenter => {
                    segment(segmenter);
                });
```
This code calls an asynchronous method on the TensorFlow.js bodySegmentation model to create a new classifier with the configuration created early. As it is asynchronous, we call `then()` to wait for the classifier. The classifier is passed to the `segmenter` parameter in the anonymous function in `then()`. At this point, we know the classifier is fully loaded so we call `segment()` and pass it the classifier.

5. Add the following code inside your `segment()` function:

```javascript
// Find the person in the image
segmenter.segmentPeople(image)
         .then(people => {
                // The colour to set pixels in the foreground (person, transparent)
                const foreground = {r: 0, g: 0, b: 0, a: 0};
                // The colour to set pixels in the background (wall, green)
                const background = {r: 0, g: 255, b: 0, a: 255};
                // Create a mask with the given colours (green background, transparent person)
                bodySegmentation.toBinaryMask(people, foreground, background)
                                .then(maskImage => {
                                      // Draw the mask on the canvas
                                      ctx.putImageData(maskImage, 0, 0);
                                });
          });
```
Check the output of your code in Chrome. You should see the original image at the top of the page and the segmented mask on the canvas. The segmented mask should look like this:
[segmented mask](url-of-image-tbd)
**Remove the background**
As the background is now a solid green, it can easily be removed by iterating through the images pixels and setting any green pixels to transparent.

1. Write a function called `isPixelGreen` that takes four parameters, `r`, `g`, `b`, and `a`, representing the colour channels in an image, including alpha. The function should return `true` if the `r` and `b` are 0 and `g` and `a` are 255.
2. Outline a function called `drawImageWithoutBackground` that takes two parameter, `image`, and `maskData`. `image` represents the original image, and `maskData` represents the segmented mask returned by the classifier.
3. Add the following code inside `drawImageWithoutBackground`:

```javascript
// Draw the image on the canvas
ctx.drawImage(image, 0, 0);
// Read the image data from the canvas, a JavaScript ImageData object
const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
// Get the pixel array from the image data
const imagePixels = imageData.data;
// Get the pixel array from the mask data
const maskPixels = maskData.data;
// Iterate through the mask pixels. If the mask pixel is green, turn the corresponding mask pixel transparent
for (let i = 0; i < maskPixels.length; i+=4) {
  if (isPixelGreen(maskPixels[i], maskPixels[i+1], maskPixels[i+2], maskPixels[i+3])) {
    imagePixels[i+3] = 0; // make the image pixel transparent by setting the alphas 
  }
}
// Draw the updated image pixels to the canvas
ctx.putImageData(imageData, 0, 0);
```
There's a lot going on in this code. In order to modify the pixels in an image, we need to get its `ImageData` object, which has a property called `data`, a 1D array representing all the pixels. The `toBinaryData()` method used in the `segment()` function returns an `ImageData` object, which will be passed to `drawImageWithoutBackground()` as the `maskData` parameter, so we already have access to the individual pixels in the segmented mask. To get the pixels from the raw image, we need to draw it on the canvas using `ctx.drawImage()`, then get its `ImageData` object using `ctx.getImageData()`.

The key part of the code above is the for loop. Conceptually, the for loop iterates through the *mask* pixels to find green pixels then it sets the alpha channel of the corresponding *image* pixel to transparent, thus removing the background and leaving the person. Notice that the for loop jumps 4 pixels on each iteration. This is because the array stores four values for each pixel, representing its colour channels (R, G, B, A). You can read more about the pixel array [in the docs](https://developer.mozilla.org/en-US/docs/Web/API/ImageData/data).

Once the background of the image is removed, the pixels are drawn to the canvas using `ctx.putImageData()`.
