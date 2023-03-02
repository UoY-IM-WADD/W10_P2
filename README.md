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

## Create a Webcam Background With TensorFlow
