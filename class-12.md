# Assorted bits of documentation:

## Read this article on the Chart.js API.

* Create stunning charts
* Pie charts, bar charts, line charts, ect
* to add the chart to our page `<canvas id="income" width="600" height="400"></canvas>`
* add the chart data 
* simple to use and flexible

## Chart.js docs: You’ll be needing these!

> It's easy to get started with Chart.js. All that's required is the script included in your page along with a single <canvas> node to render the chart.

Read the following articles on the Canvas API.
>  a <canvas> looks like the <img> element, but it doesn't have the src and alt attributes. Indeed, the <canvas> element has only two attributes, width and height. These are both optional and can also be set using DOM properties. When no width and height attributes are specified, the canvas will initially be 300 pixels wide and 150 pixels high.
Basic usage
*  if the CSS sizing doesn't respect the ratio of the initial canvas, it will appear distorted.
* It is always a good idea to supply an id because this makes it much easier to identify it in a script.
* 1. fallback content: insert alternate content inside the `<canvas>` element so if the browser is unsupoported, it will ignore the `<canvas>` element and go on to the fallback. 
Example: `<canvas id="stockGraph" width="150" height="150">`
  `current stock price: $3.15 + 0.15`
`</canvas>`

`<canvas id="clock" width="150" height="150">`
  `<img src="images/clock.png" width="150" height="150" alt=""/>`
`</canvas>`
* Providing a useful fallback text or sub DOM helps to make the canvas more accessible.

## Drawing shapes with canvas
reference: `https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes`

with this canvas we can make: 
* the grid
* rectangles
* paths
* triangle
* move the pen
* lines
* Arcs
* Bezier and quadratic curves
* cubic bezier curves
* rectangles
* combinations*******
* path2D objects
* Using SVG paths

## Applying styles and colors
> When you set the strokeStyle and/or fillStyle property, the new value becomes the default for all shapes being drawn from then on. For every shape you want in a different color, you will need to reassign the fillStyle or strokeStyle property.
We use for loops to draw a grid of rectangles. Use variable for color
This is so interesting! Finally starting to see how all of this makes an interavtive website!
> 
## Drawing text
1. The text is filled using the current fillStyle.

`function draw() {`
 ` var ctx = document.getElementById('canvas').getContext('2d');`
  `ctx.font = '48px serif';`
  `ctx.fillText('Hello world', 10, 50);`
`}`

2. The text is filled using the current strokeStyle.

`function draw() {`
  `var ctx = document.getElementById('canvas').getContext('2d');`
  `ctx.font = '48px serif';`
  `ctx.strokeText('Hello world', 10, 50);`
`}`

3. font = value
The current text style being used when drawing text. This string uses the same syntax as the CSS font property. The default font is 10px sans-serif.
textAlign = value

4. Text alignment setting: Possible values: start, end, left, right or center. The default value is start.
textBaseline = value

5. Baseline alignment setting. Possible values: top, hanging, middle, alphabetic, ideographic, bottom. The default value is alphabetic.
direction = value

6. Directionality. Possible values: ltr, rtl, inherit. The default value is inherit.

