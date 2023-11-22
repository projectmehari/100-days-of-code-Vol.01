# Day 91

Tags: p5.js
Date: October 30, 2023
Status: Done

Task of the day

- Learn p5.js
- Introduction to interaction in p5.js

---

### **Random**

If you want to add some unpredictability to your sketch, `random()` is the perfect function for you! This is especially helpful when you are tired of making decisions and are happy to let computation make some of them for you.

The `random()` function returns a random value every time it is called. There are a few ways to write this function:

- `random()` returns a value between 0 and 1.
- `random(max)` returns a value between 0 and `max`value, but excluding the `max` value.
- `random(min, max)` returns a value between `min`value and `max` value, but excluding the `max` value.
- If the `random()` function is used inside the `draw()`loop, the `random()` function generates a different randomized value every time the `draw()` function runs.

```jsx
let circleX;
let circleY;

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(0);
  noStroke();
  frameRate(10);
}

function draw(){
  // TODO: Set the elliipse's x position to be a random position
let circleX = random(0, width);
let circleY = random(0, height);
fill(random(0, 256));
ellipse(circleX, circleY, 50, 50);

}
```

---

### **Creating Custom Functions**

p5.js is built on [functions](https://www.codecademy.com/learn/introduction-to-javascript/modules/learn-javascript-functions). For example, the `draw()` loop is a function used in every sketch. All shapes are drawn using functions such as `ellipse()`, `rect()` and `line()`.

As a reminder, you can define functions by writing:

```jsx
function nameOfFunction (x, y, z){
   // Do something when this function is called
}

```

In the code above, `x`, `y`, and `z` are variables that represent the function’s parameters. *Parameters* are a way to introduce variations into your functions. For example, let’s say you want to draw three clouds, but you want each cloud’s location and size to be different. To do this, you would need to write parameters for your `makeCloud()` function. When you call the function, the variables get replaced with the specific values passed into that  `makeCloud()` function call.

Take a look at the **cloud.js** file to your right. See how the function’s parameters are used to create variations. Keep in mind that p5.js runs through the program line by line, from top to bottom. Every time the program reaches a `makeCloud()` function call, the program jumps to the function definition outside of the `draw()` loop.

```jsx
let xPos = 0;
let yPos;
let cloudSize;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(0);

  makeCloud(xPos + width / 2, 50, 50);
  makeCloud(xPos + width / 7, 210, 140);
  makeCloud(xPos + width / 1.5, 340, 70);
}

function makeCloud(xPos, yPos, cloudSize) {
  noStroke();
  fill(255);

  ellipse(xPos, yPos, cloudSize);
  ellipse(xPos + cloudSize / 2, yPos, cloudSize);
  ellipse(xPos + cloudSize, yPos, cloudSize);
  ellipse (xPos + cloudSize/2, yPos - cloudSize/3, cloudSize);
}
```

---

### Review

- A frame is the equivalent to a loop through the `draw()` function
- A p5.js sketch runs at 60 frames per second, meaning that the `draw()` function executes 60 times per second.
- You can use the `framerate()` function to alter how many frames are displayed in a second, also know as Frames Per Second (FPS).
- Increment and decrement values to create continuous motion.
- Conditional statements can be used to create more complicated animation sequences.
- Create variables to increment or decrement the speed of a moving object.
- Invert the direction of the moving object by using conditionals and multi-playing -1 to existing speed values
- the `random()` function is used for creating unpredictable but smoother movements
- Create your own functions so you code is modular and reusable.

---

### Grouping and Transforming shapes

### Review

- The `rectMode()`function specifies the origin point from which the rectangle is drawn.
- `rectMode(CENTER)`specifies that the x and y coordinates passed into the `rect()` function are for the rectangle’s center.
- `rectMode(CORNER)`specifies that the x and y coordinates passed into the `rect()` function are for the rectangle’s top left corner. If you don’t specify the `rectMode()`, p5.js will automatically assign the origin of rectangles to be the `CORNER`.
- The `ellipseMode()`function specifies the origin point from which the ellipse is drawn.
- `ellipseMode(CENTER)`specifies that the x and y coordinates passed into the `ellipse()`function are for the center of the shape. If you don’t specify the `ellipseMode()`, p5.js will automatically assign the origin of ellipses to be `CENTER`.
- `ellipseMode(CORNER)`specifies that the x and y coordinates passed into the `ellipse()`function are for the top left corner.
- The `translate()`function changes the origin of the p5.js canvas to the coordinates passed to the function.
- The `rotate()` function rotates the p5.js coordinate system, not a specific shape. The `rotate()` function requires one argument—the angle for rotation in radians.
- The `radians()` function converts a degree measurement into radians.
- The `angleMode()`function changes whether angle values are interpreted as `RADIANS`or `DEGREES`.
- The `scale()` function sets the size of the p5.js canvas and all the elements on it. Scale values are written in decimal percentages.
- The `shearX()` function horizontally angles a shape by the amount specified in the argument.
- The `shearY()` function vertically angles a shape by the amount specified in the argument.
- The `push()` function saves the current drawing styles and transformations. The `pop()` function restores it back to the settings that were in effect prior to the most recent call to `push()`.
- The order makes a difference when combining multiple transformations.

---

### Introduction to interaction in p5.js

### Review

- How to use `mouseX` and `mouseY`to track mouse position, modify shapes, determine shape positions, and more!
- Using the built-in `mouseIsPressed` variable to detect mouse presses and trigger events from the presses.
- How to use the `mousePressed()`function to trigger events when the mouse button is pressed over the current canvas element.
- How to use the `dist()` function to calculate the distance between two points.
- Using the `key` variable to store the alphanumeric value of the most recent key pressed.
- Detecting special keys and ASCII character values with the `keyCode` variable.
- How to use the `keyIsPressed`boolean to detect general key presses.
- Using the `keyPressed()` function to trigger events when a key is pressed.

---

### Introduction to images and videos

**Loading and drawing image**

Unlike the primitive shapes we’ve drawn so far, media, like images, are considered external assets. To include them in our sketches, we will need to load them using special, built-in p5.js functions.

To load an image, use the `loadImage()` function. It requires one argument—the path to the image in your working directory.

```jsx
img = loadImage('imageName.jpg');

```

The `loadImage()` function returns a [p5.js Image](https://p5js.org/reference/#/p5.Image) element. Saving it to a variable lets us reuse the loaded image as many times as we want.

After loading an image, we use the `image()` function to draw it. The function requires three arguments: the p5.js Image element and the x and y positions where the image should be drawn on the canvas.

```jsx
//Draw img to the top left corner of the canvas
image(img, 0, 0);

```

Optionally, the `image()` function can take other arguments. We can also resize the drawn image to a certain width and height, as follows:

```jsx
let drawnWidth = 100;
let drawnHeight = 100;
image(img, 0, 0, drawnWidth, drawnHeight);

```

We can also add an additional four arguments to draw a cropped region of the image—check out the [p5.js documentation](https://p5js.org/reference/#/p5/image) to learn more.

You can also load and draw animated GIFs into the canvas using `loadImage()` and `image()`. To have them animate, you specifically need to put them inside the `draw()` loop. They’re essentially multiple images packed into one, so calling `image()`in the `draw()` loop will draw the latest frame of the GIF, allowing it to animate.

```jsx
draw() {
  image(myAnimatedGIF, 0, 0);
}

```

Because drawing an image requires it to be completely loaded, it’s important to note how and when these functions are called.

Loading images takes time. In most cases, the `loadImage()` function won’t finish loading an image before the next lines of code are run—including any code that is supposed to draw the image.

Sometimes this is OK, but it can also potentially lead to unintended behavior. Later, we’ll learn to work around this problem by having more control over the loading of the images.

---

### **Videos**

Now that we can add images into the canvas let’s learn how to add another major type of media: videos!

To create a p5.js video element, use the `createVideo()` function. It requires the video file’s path in your working directory. Here, we’ll use a video with the .mp4 format, which is a video file format that’s well-supported across most browsers.

```
let video;
video = createVideo('myVideo.mp4');

```

As with images, we can store video elements as variables. Typically, we’ll do this in a place like the `preload()`function so that we can use it later on in our sketch.

To play a video, you can use the `.play()` method:

```
video.play();

```

Leveraging HTML and JavaScript’s existing support for videos, the `createVideo()` function displays an HTML video element on the page, but not within the sketch itself.

To display the video directly within the p5 sketch, we can reuse the `image()` function from before:

```
image(video, 0, 0);

```

It may be confusing to use a function called ‘image’ to draw videos—but it makes sense when we think of a video as a sequence of images. When called, the `image()` function draws the current frame of the video on the canvas. When placed in the `draw()` loop, we can create the illusion of a video playing, frame-by-frame.

Like with drawing images, you can resize the drawn video by adding two more parameters:

```
let drawnWidth = 100;
let drawnHeight = 100;
image(video, 0, 0, drawnWidth, drawnHeight);

```

To hide the original HTML video element, we can use the `.hide()`method:

```
video.hide()

```

This makes the original video invisible—but it doesn’t delete it! You’ll still be able to hear the video’s sound unless you turn off its volume. We’ll get to that in the next exercise!

Note that the `.hide()` method will hide the video drawn on the canvas as well unless at any point you play the video. Until then, no video frames will draw to the canvas.

---

### **Video Options**

Now that we can add videos to the canvas let’s take a look at some extra options p5.js gives us to control video options and playback. These options also build off of HTML and JavaScript’s existing support for video playback.

We already learned how to use the `.play()` method to play a video. In actuality, there is another way to get a video to play: the `.loop()` method. Whereas the `.play()` method only plays a video once, the `.loop()`method will play a video and loop it infinitely.

```jsx
video.loop();

```

Because of how these methods work behind-the-scenes in JavaScript, there are some quirks that can lead to common problems. One of them is that calling `.play()` or `.loop()` way too many times, such as in every iteration of the `draw()` loop, can cause errors. In general, it’s best to call them in `setup()`, or call them in response to user input, like mouse clicks.

To stop a playing or looping video, use the `.stop()` method.

```jsx
video.stop();

```

The `.stop()` method stops the video and returns it to the starting frame of the video. To pause the video at the current frame—so that you can later resume it where you left off—use the `.pause()` method:

```jsx
video.pause();

```

To change the volume of the video’s sound, use the `.volume()` method. It takes in a decimal number ranging from 0 to 1, with 0 being no volume and 1 being maximum volume.

```jsx
video.volume(0); // Mutes the sound
video.volume(1); // Plays sound at max volume
video.volume(0.5); //Plays sound at half volume

```

```jsx
let video;
let isVolumeOn = true;
let videoPath = 'https://static-assets.codecademy.com/Courses/Learn-p5/media/codeyVlog.mp4';

function preload(){
  video = createVideo(videoPath);
}

function setup() {
  createCanvas(480, 270);
  //Creates a background with a play symbol
  background(0);
  triangle(215, 110, 275, 140, 215, 170);
  //Hides the original HTML video element
  video.hide();
}

function draw() {
  image(video, 0, 0, 480, 270);
}

function pressPlayButton() {
  //TODO: Play video here:
video.play();
}

function pressPauseButton() {
  //TODO: Pause video here:
video.pause();
}

function pressToggleVolumeButton() {
  if (isVolumeOn) {
    //TODO: Turn volume off here:
    video.volume(0); //Turns sound off
video.volume(1); //Turns sound to max volume

  } else {
    //TODO: Turn volume on here:

  }
  isVolumeOn = !isVolumeOn;
}
```

---

### **Filters**

Adding photos and videos into the canvas is cool, but the real fun comes when we add effects to them through tools like filters.

Filters in p5.js work in two ways: across the entire canvas and applied to individual images.

To apply a filter across the canvas, use the `filter()` function. It requires the type of filter, which can be one of eight different types as defined by p5.js. For a complete list, visit the [p5.js reference on filters](https://p5js.org/reference/#/p5/filter).

For example, to add a `GRAY` filter across the canvas, use:

```
filter(GRAY);

```

![https://static-assets.codecademy.com/Courses/Learn-p5/media/grayFilter.gif](https://static-assets.codecademy.com/Courses/Learn-p5/media/grayFilter.gif)

Certain filter types require an additional numerical argument. For example, the `POSTERIZE` filter, which reduces the number of colors in the image, requires a value between 2 and 255.

```
filter(POSTERIZE, 3);

```

![https://static-assets.codecademy.com/Courses/Learn-p5/media/posterizeFilter.gif](https://static-assets.codecademy.com/Courses/Learn-p5/media/posterizeFilter.gif)

The `filter()` function applies the filter to everything drawn on the canvas before it’s called—this lets us layer filters together, combining them with ones that were called previously.

![https://static-assets.codecademy.com/Courses/Learn-p5/media/grayAndPosterizeFilter.gif](https://static-assets.codecademy.com/Courses/Learn-p5/media/grayAndPosterizeFilter.gif)

It also lets us apply filters to certain parts of the canvas—for example, we can apply a filter to the entire canvas, then draw new elements that’ll be unaffected.

![https://static-assets.codecademy.com/Courses/Learn-p5/media/layersFilters.gif](https://static-assets.codecademy.com/Courses/Learn-p5/media/layersFilters.gif)

To apply filters across an individual p5 image element, use the `.filter()` method. You’ll need to call this before drawing the image.

```
//Invert colors in an image
img.filter(INVERT);
image(img, 0, 0);

```

![https://static-assets.codecademy.com/Courses/Learn-p5/media/imageFilter.gif](https://static-assets.codecademy.com/Courses/Learn-p5/media/imageFilter.gif)

We can’t, however, apply filters to individual video elements (though you could instead draw a video to the canvas, then add a filter to the entire canvas).

A weakness of the `filter()` function is its slow performance—especially when called frequently. Later, we’ll learn how to achieve similar effects (and more!) with pixel manipulation.

```jsx
let img1, img2, img3, img4;

let imagePath = `https://static-assets.codecademy.com/Courses/Learn-p5/media/cutePuppySquare.jpg`;

function preload() {
  img1 = loadImage(imagePath);
  img2 = loadImage(imagePath);
  img3 = loadImage(imagePath);
  img4 = loadImage(imagePath);
}

function setup() {
  createCanvas(400, 400);
  //TODO: Apply filters here
  img1.filter(GRAY);
  img2.filter(INVERT);
  img3.filter(POSTERIZE, 4);
  img4.filter(THRESHOLD);
  //Draws the 4 images to the canvas
  image(img1, 0, 0, 200, 200);
  image(img2, 0, 200, 200, 200);
  image(img3, 200, 0, 200, 200);
  image(img4, 200, 200, 200, 200);
}
```

---

### **Introduction to Pixel Manipulation**

We can also use p5.js to manipulate images and videos, down to the pixel. p5.js offers built-in functions to do this: `get()` and `set()`.

The `get()` function accesses the color of a specific pixel on the canvas. When given a pixel location, it returns the color of that pixel as an array of four numbers, representing the red, green, blue, and alpha (RGBA) values.

```jsx
let pixelColor = get(28, 35); // Returns [r, g, b, a], where r, g, b, a are values between 0 and 255

```

![https://static-assets.codecademy.com/Courses/Learn-p5/media/get.png](https://static-assets.codecademy.com/Courses/Learn-p5/media/get.png)

Alternatively, the `get()` function also can retrieve regions of the canvas, returning them as a p5.js image element.

```jsx
// Using get() to access a portion of canvas
let x = 0; let y = 0;
let w = 100; let h = 100;
let partOfCanvas = get(x, y, w, h); // Returns a region starting at (x, y) that's w-pixels wide and h-pixels high

```

When provided no arguments, it retrieves the entire canvas as a p5.js image element.

```jsx
// Using get() to access entire canvas
let entireCanvas = get();

```

The `set()` function sets a pixel at a given location on the canvas to a new color.

```jsx
let red = [255, 0, 0, 255];
set(28, 35, red); // Sets pixel at (28, 35) to red

```

![https://static-assets.codecademy.com/Courses/Learn-p5/media/set.png](https://static-assets.codecademy.com/Courses/Learn-p5/media/set.png)

The color can be in several formats. Above, we’re using an array of 4 RGBA values, but you can also use a single greyscale value or a [p5.js color element](https://p5js.org/reference/#/p5/color).

Just calling the `set()` function doesn’t change what you see—to reflect changes onto the canvas, you need to use the `updatePixels()`function after the `set()` call.

```jsx
let red = [255, 0, 0, 255];
set(0, 0, red); // Pixel is not actually changed on screen
updatePixels(); // Now pixel is changed!

```

If you use `set()` multiple times, calling `updatePixels()` once will reflect all those changes.

```jsx
let red = [255, 0, 0, 255];
set(0, 0, red);
set(0, 1, red);
updatePixels(); // Both pixels are updated

```

The `get()` and `set()` functions also work as methods on individual image or video elements.

When using the `.set()` method on images or videos, you’ll need to call it, along with the `.updatePixels()`method, before you draw them to the canvas.

```jsx
let red = [255, 0, 0, 255];
img.set(50, 50, red); // Pixel is not actually changed in our image element
img.updatePixels(); // Now pixel is changed in our pixel element
image(img, 0, 0); // Now our modified image element is on the screen

```

Because they’re time-intensive, `get()` and `set()` are best suited for conveniently accessing a few pixels at a time. Later, we’ll see how to do larger-scale manipulations, such as accessing pixels in very large images and/or doing manipulations repeatedly in the `draw()` loop.

---

### **Manipulating the Pixels Array**

Once we have the `pixels` array, we need to know how to read and write to it. That requires correctly indexing into it to get the color values for each pixel.

Because each pixel has four color values—starting with red—we can use the following equation to find the index of the red value for a pixel at location (x,y), on a canvas that’s `width` pixels wide.

```jsx
let indexOfRed = (x + y * width) * 4;

```

Image or video elements have their own dimensions, accessed through the `.width` and `.height` properties. Accordingly, their equations will be slightly different:

```jsx
let indexOfRedForImage = (x + y * img.width) * 4;
let indexOfRedForVideo = (x + y * video.width) * 4;

```

In this example, we’ll access the `.pixels` array of an image. With the index of the red value, we can then get each color value, keeping in mind the R-G-B-A sequence.

```jsx
let red = img.pixels[indexOfRed];
let green = img.pixels[indexOfRed + 1];
let blue = img.pixels[indexOfRed + 2];
let alpha = img.pixels[indexOfRed + 3];

```

To set a new color for that pixel at (x,y), set its RGBA elements in the `.pixels` array to new values.

```jsx
img.pixels[indexOfRed] = 255; // Red
img.pixels[indexOfRed + 1] = 0; // Green
img.pixels[indexOfRed + 2] = 0; // Blue
img.pixels[indexOfRed + 3] = 255; // Alpha
img.updatePixels();

```

Above, we set the pixel to red, i.e. `[255, 0 , 0, 255]`. Again, we must call the `.updatePixels()` method (or `updatePixels()` function, if we’re manipulating the canvas) to reflect changes.

Most likely, we’ll want to manipulate many pixels—that’s what the `pixels`array is designed for!

```jsx
//Double "for" loop to iterate through pixels, row by row:

let stepSize = 1;
//Loop through rows
for (let y = 0; y < img.height; y += stepSize){
  //Loop through columns
  for (let x = 0; x < img.width; x +=  stepSize){
    //Get index # of red value for pixel
    let indexOfRed = (x + y * img.width) * 4;
    //Set every pixel to black
    img.pixels[indexOfRed] = 0; // Red
    img.pixels[indexOfRed + 1] = 0; // Green
    img.pixels[indexOfRed + 2] = 0; // Blue
    img.pixels[indexOfRed + 3] = 255; // Alpha
  }
}
img.updatePixels();

```

Here, we used a double `for` loop, bounded by the image’s width and height, to iterate through every pixel in the image, row-by-row. By setting its RGBA values accordingly, each pixel is set to the color black, i.e. `[0, 0, 0, 255]`. Depending on the application, you might want to go through every couple of pixels, instead of every single one. To do that, you can increase the value of the `stepSize` variable.

We called the `.updatePixels()`method outside and after this loop so that we can update all of the changes we made to `.pixels` with a single call. If we call it inside the loop, we might crash our sketch!

```jsx
let video;
let videoPath = 'https://static-assets.codecademy.com/Courses/Learn-p5/media/UFO.mp4';

function preload(){
  video = createVideo(videoPath);
}

function setup() {
  //Set pixel density to 1
  pixelDensity(1);
  createCanvas(480, 270);
  //Creates a background with a play symbol
  background(0);
  triangle(215, 110, 275, 140, 215, 170);
  //Hides the original HTML video element
  video.hide();
}

function draw() {
  //Load video pixels
  video.loadPixels();
  //Iterate through all pixels in the video
  let stepSize = 1;
  for (let y = 0; y < video.height; y += stepSize){
    for (let x = 0; x < video.width; x += stepSize){
      //TODO: Manipulate pixels array
      let indexOfRed = (x + y * video.width) * 4;
      video.pixels[indexOfRed + 1] = random(100);
    }
  }
  //TODO: Update the pixels in the video
  video.updatePixels();
  //Draw the video to the canvas
  image(video, 0, 0, 480, 270);
}
```

---

### Review

- The `loadimage()` function is used to load an external image into your p5 Sketch. The function must be provided with the path to the image as an argument in string format.
- The `preload()` function is meant to hold any code for loading media that needs to be completely loaded before the `setup()` function and `draw()` loop run.
- The `image()` function draws an image to the canvas, taking in the given image element and the x and y location of where the image should be drawn.
- Optionally, arguments for width, height, and crop dimensions can be given to the function.
- The `createVideo()` function creates an HTML video element that is displayed outside of the sketch. It takes in a single path to a video as a string.
- p5.js supports various methods that affect playback of videos, such as `.loop()`, `.play()`, .`stop()`, `.pause()`, and `.volume()`.
- Filters are a way to apply effects all-over an entire canvas or on an image element. Both the `filter()` function for canvases and `.filter()` method for images require the type of filter as an argument.
- Certain filter types require an additional numerical argument.
- While filters can be used on images, they can not be applied to individual video elements.
- The `get()` function accesses the pixel color on the canvas at a specific x,y coordinate, as an array of four values representing the red, green, blue, and alpha values.
- Alternately, the `get()` function can return a region of the canvas as an image element—when provided with two additional parameters for width and height, it returns the region starting at the x, y position, bounded by the width and height.
- When provided with no arguments, it returns the entire canvas region as an image.
- The `set()` function sets a pixel at a given x, y coordinate to a color, which can be an array of four RGBA values, a single greyscale value, or a p5.js color element.
- To reflect changes made with the `set()` function, you must call the `updatePixels()` function.
- The `pixels` array provides a faster way to read and modify pixels. It lists the R, G, B, A values for every pixel in an image or canvas in one single array.
- Before accessing the pixels array, you must load the pixels with the `loadPixels()` function.
- After making modifications to the pixels array, you must call `updatePixels()` to see those changes reflected.