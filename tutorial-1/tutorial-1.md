
# Tutorial 1 - WebGL Canvas

### Step 0 - What is WebGL?
WebGL (Web Graphics Library) is a great way to learn the basics of Computer Graphics using your web browser. It is an offshoot of OpenGL, a Computer Graphics library used in non-web programs. 

### Step 1 - HTML Template
HTML (Hyper Text Markup Language) is the foundation for how webpages are built. To create a basic webpage, save the following code to "tutorial-1.html" on your computer and run it in your web browser.

```html
<!-- HTML Template -->
<!DOCTYPE HTML>
<html lang="en">

<head>
  <title>Tutorial 1 - WebGL Canvas</title>
</head>

<header>
    Below is a basic WebGL Canvas!
</header>

</html>
```

### Step 2 - WebGL Canvas (JavaScript)
Now we will add the WebGL canvas. Most of your WebGL code will be written in JavaScript. JavaScript is the programming language that allows for interactive / dynamic webpages. Create another file called "tutorial-1.js". To make a WebGL canvas, we will need two variables: ```gl``` and ```canvas```. ```gl``` is the JavaScript WebGL context where the brains WebGL reside. As the name implies, the ```canvas``` is where WebGL will draw graphics onto your computer. 

```javascript
// Initialize variables
var gl; // WebGL context (where WebGL code runs)
var canvas; // HTML canvas (where WebGL context is displayed)
```

Now we need to initialize these. We will use two functions: ```startup()``` and ```createGLContext(canvas)```. ```startup()``` will be called from the HTML file when the canvas is created. ```createGLContext(canvas)``` is the code that talks with your web browser to setup WebGL.

```javascript
// Initializes WebGL context
function createGLContext(canvas) {
  var names = ["webgl", "experimental-webgl"];
  var context = null;
  for (var i = 0; i < names.length; i++) {
    try {
      context = canvas.getContext(names[i]);
    } catch (e) { }
    if (context) {
      break;
    } 
  }
  if (context) {
    context.viewportWidth = canvas.width;
    context.viewportHeight = canvas.height;
  } else {
    alert("Failed to create WebGL context!");
  }
  return context;
}

// Setup to startup WebGL and link to HTML
function startup() {
  canvas = document.getElementById("glCanvas");
  gl = createGLContext(canvas);
  gl.clearColor(0.0, 0.0, 0.0, 1.0);
  gl.viewport(0, 0, gl.viewportWidth, gl.viewportHeight);
  gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT);
}
```

### Step 3 - Link HTML & JavaScript
To link the HTML and JavaScript, we need to import "tutorial-1.js" into the HTML webpage. Add the following to "tutorial-1.html" within the ```<html></html>``` tags.

```html
<!-- Import JavaScript files -->
<script src="tutorial-1.js"></script>
```

We also need to create an HTML canvas so WebGL has somewhere to draw into. The HTML and JavaScript canvasses are linked through the ```id="glCanvas"``` tag. When the HTML canvas is created, we call the ```startup()``` function.

```html
<!-- HTML canvas element where WebGL canvas is rendered -->
<body onload="startup();">
  <canvas id="glCanvas" width="500" height="500"></canvas>
</body>
```

Once these are all put together, run your code. You should see a black box (your WebGL canvas)! Try changing the numbers in ```gl.clearColor()``` to see different RGBA values.

### Step 4 - Tips & Tricks
```Ctrl + Shift + I``` lets you inspect web pages. This will let you view the webpage's code and will also show you the console for error messages when you are debugging.

### Step 5 - Full Code
Here you can find the [full code](https://github.com/Greenninja4/graphics/tutorial-1)