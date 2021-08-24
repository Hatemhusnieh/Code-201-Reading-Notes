# Chart.js, Canvas
## Chart.js API.
Charts are far better for displaying data visually than tables and have the added benefit that no one is ever going to press-gang them into use as a layout tool. They’re easier to look at and convey data quickly, but they’re not always easy to create.  
  
Chart.js is a plugin, that make the creation of charts easy business. It helps with all kind of charts like for example bar charts, line charts, pie charts and more .  
  
### Setting up
The first thing we need to do is download Chart.js. Copy the Chart.min.js out of the unzipped folder and into the directory you’ll be working in. Then create a new html page and import the script:  
![chart.js](imgs/chart.png)  

### Drawing  
* to draw a line use `<canvas>` element, then retrieve it and write the data which you want to retrieve.  
![line](imgs/line.png) ![lineSccript](imgs/linee.png) ![lineDta](imgs/lineee.png)   

* to draw a pie chart is like the previous steps the difference is using another method (instead of `.line()` use `.Pie()`)  
![pei](imgs/pie.png) ![peiScript](imgs/piee.png) ![pieDta](imgs/pieee.png)   
  
* Also we can draw a Bar chart by the previous way, but using this time hte `Bar()` method.
  
## Canvas API 
### Basic usage of canvas  
- the `<canvas>` is element is like an image but without the `src` and `alt` attributes.  

- the `<canvas>` element has only two attributes, width and height and they can also be neglected and the browser will assume the `width` of **300 px** and `height` of **150 px**  

- It is always a good idea to supply an id for the `<canvas>` because this makes it much easier to identify it in a script, but it is still a global attribute for `HTML`  

- The `<canvas>` element can be styled just like any normal image (margin, border, background…), and through `CSS`. However if the rules of `CSS` does not respect the chart dimension, then the chart will be distorted.  

- Providing fallback content is very straightforward: just insert the alternate content inside the `<canvas>` element. Browsers that don't support `<canvas> `will ignore the container and render the fallback content inside it. Browsers that do support `<canvas>` will ignore the content inside the container, and just render the canvas normally.  

- As a consequence of the way fallback is provided, unlike the `<img>` element, the `<canvas>` element requires the closing tag (`</canvas>`). Unless the browser will not render the content.

- The` <canvas>` element creates a fixed-size drawing surface that exposes one or more rendering contexts, which are used to create and manipulate the content shown.  

### Drawing shapes with canvas
- Normally 1 unit in the grid corresponds to 1 pixel on the canvas. The origin of this grid is positioned in the top left corner at coordinate (0,0). All elements are placed relative to this origin. So the position of the top left corner of the blue square becomes x pixels from the left and y pixels from the top, at coordinate (x,y).  

- we have three **functions** that creates rectangles:  
    1. `fillRect(x, y, width, height)`:    
        - Draws a filled rectangle.
    1. `strokeRect(x, y, width, height)`:  
        - Draws a rectangular outline.
    1. `clearRect(x, y, width, height):`  
        - Clears the specified rectangular area, making it fully transparent.

A **path** is a list of points, connected by segments of lines that can be of different shapes, curved or not, of different width and of different color.  
  
- to draw a path:
    1. First, you create the path
    1. Then you use **drawing commands** to draw into the path.
    1. Once the path has been created, you can stroke or fill the path to render it.

- `beginPath()`: Creates a new path. Once created, future drawing commands are directed into the path and used to build the path up.

- **Path methods**: Methods to set different paths for objects.
    - `closePath()` :Adds a straight line to the path, going to the start of the current sub-path.
    - `stroke()`:Draws the shape by stroking its outline.
    - `fill()` :Draws a solid shape by filling the path's content area

- `moveTo(x, y)`: Moves the pen to the coordinates specified by x and y.

- `lineTo(x, y)`: Draws a line from the current drawing position to the position specified by **x** and **y**

- `arc(x, y, radius, startAngle, endAngle, counterclockwise)` : Draws an arc which is centered at (x, y) position with radius r starting at startAngle and ending at endAngle going in the given direction indicated by counterclockwise (defaulting to clockwise). 
 - `arcTo(x1, y1, x2, y2, radius)` :Draws an arc with the given control points and radius, connected to the previous point by a straight line.

 - `quadraticCurveTo(cp1x, cp1y, x, y)` :Draws a quadratic **Bézier** curve from the current pen position to the end point specified by x and y, using the control point specified by cp1x and cp1y.

 - `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)` :Draws a cubic Bézier curve from the current pen position to the end point specified by x and y, using the control points specified by (cp1x, cp1y) and (cp2x, cp2y).

 - `rect(x, y, width, height)` :Draws a rectangle whose top-left corner is specified by (x, y) with the specified `width` and `height`

 - `Path2D()` :The `Path2D()` constructor returns a newly instantiated **Path2D** object, optionally with another path as an argument (creates a copy), or optionally with a string consisting of SVG path data.

 -` Path2D.addPath(path [, transform])` :Adds a path to the current path with an optional transformation matrix.  

### Applying styles and colors  
  
To apply colors to a shape,  

- `fillStyle = color`: Sets the style used when filling shapes.

- `strokeStyle = color`: Sets the style for shapes' outlines.

- When you set the `strokeStyle` and/or `fillStyle` property, the new value becomes the **default** for all shapes being drawn from then on. For every shape you want in a different color, you will need to _**reassign**_ the `fillStyle` or `strokeStyle` property.  

- `globalAlpha = transparencyValue`: Applies the specified **transparency** value to all future shapes drawn on the canvas. The value must be between **0.0** (fully transparent) to **1.0** (fully opaque). This value is 1.0 (fully opaque) by default.
  
- `lineWidth = value`: Sets the width of lines drawn in the future.

- `lineCap = type`: Sets the appearance of the ends of lines.

- `lineJoin = type`: Sets the appearance of the "corners" where lines meet.

- `miterLimit = value`: Establishes a limit on the miter when two lines join at a sharp angle, to let you control how thick the junction becomes.

- `getLineDash()`: Returns the current line dash pattern array containing an even number of non-negative numbers.

- `setLineDash(segments)`: Sets the current line dash pattern.

- `lineDashOffset = value`: Specifies where to start a dash array on a line

- For the `lineCap` property:  
    - `butt`: The ends of lines are squared off at the endpoints.
    - `round`: The ends of lines are rounded.
    - `square`: The ends of lines are squared off by adding a box with an equal width and half the height of the line's thickness.

- For the `lineJoin` property:  
    - `round`: Rounds off the corners of a shape by filling an additional sector of disc centered at the common endpoint of connected segments. The radius for these rounded corners is equal to half the line width.
    - `bevel`: Fills an additional triangular area between the common endpoint of connected segments, and the separate outside rectangular corners of each segment.
    - `miter`: Connected segments are joined by extending their outside edges to connect at a single point, with the effect of filling an additional lozenge-shaped area. This setting is effected by the miterLimit property which is explained below.

- `createLinearGradient(x1, y1, x2, y2)`: Creates a linear gradient object with a starting point of (x1, y1) and an end point of (x2, y2).

- `createRadialGradient(x1, y1, r1, x2, y2, r2)`: Creates a radial gradient. The parameters represent two circles, one with its center at (x1, y1) and a radius of r1, and the other with its center at (x2, y2) with a radius of r2.

- `createConicGradient(angle, x, y)`: Creates a conic gradient object with a starting angle of angle in radians, at the position (x, y).

- `gradient.addColorStop(position, color)`: Creates a new color stop on the gradient object. The position is a number between 0.0 and 1.0 and defines the relative position of the color in the gradient, and the color argument must be a string representing a **CSS** `<color>`, indicating the color the gradient should reach at that offset into the transition.

- `createPattern(image, type)`: Creates and returns a new canvas pattern object. `image` is a `CanvasImageSource` (that is, an `HTMLImageElement`, another canvas, a `<video>` element, or the like. `type` is a string indicating how to use the image.

- the type in the previous function can be:  
    - `repeat`: Tiles the image in both vertical and horizontal directions.
    - `repeat-x`: Tiles the image horizontally but not vertically.
    - `repeat-y`: Tiles the image vertically but not horizontally
    - `no-repeat`: Doesn't tile the image. It's used only once.

- `shadowOffsetX = float`: Indicates the horizontal distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0

- `shadowOffsetY = float`: Indicates the vertical distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.

- `shadowBlur = float`: Indicates the size of the blurring effect; this value doesn't correspond to a number of pixels and is not affected by the current transformation matrix. The default value is 0.

- `shadowColor = color`: A standard CSS color value indicating the color of the shadow effect; by default, it is fully-transparent black.

### Drawing text  

- `fillText(text, x, y [, maxWidth])`: Fills a given text at the given (x,y) position. Optionally with a maximum width to draw

- `strokeText(text, x, y [, maxWidth])`: Strokes a given text at the given (x,y) position. Optionally with a maximum width to draw

### Styling text

- `font = value`: The current text style being used when drawing text. This string uses the same syntax as the **CSS** `font` property. The default font is 10px sans-serif.

- `textAlign = value`: Text alignment setting. Possible values: `start`, `end`, `left`, `right` or `center`. The default value is `start`.

- `textBaseline = value`: Baseline alignment setting. Possible values: `top`, `hanging`, `middle`, `alphabetic`, `ideographic`, `bottom`. The default value is `alphabetic`

- `direction = value`: Directionality. Possible values: `ltr`, `rtl`, `inherit`. The default value is `inherit`.

- `measureText()`: Returns a `TextMetrics` object containing the width, in pixels, that the specified text will be when drawn in the current text style.

- 