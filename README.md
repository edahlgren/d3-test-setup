# Test your d3.js setup

## Launch a d3.js demo

[Download](https://github.com/edahlgren/d3-test-setup/raw/master/test-setup.zip) the test files and unpack them:

```
$ unzip test-setup.zip
```

The test directory contains these files:

| file | description         |
| ---- | ------------------- |
| index.html | An HTML skeleton, loads d3 |
| data/database.json | A simple database of circles |
| js/main.js | The d3.js javascript program | 
| css/main.css | Minimal HTML styling |

Using the [nodejs http-server](https://www.npmjs.com/package/http-server), serve these files:

```
$ cd YOUR_DIRECTORY
$ http-server -c-1
```

You should see something like this:

![http-server startup output](https://raw.githubusercontent.com/edahlgren/d3-test-setup/master/http-server-startup.png)

Go to the web address in your browser (http://127.0.0.1/8080). You should see a webpage with five circles:

![html output](https://raw.githubusercontent.com/edahlgren/d3-test-setup/master/d3-test-setup.png)

You've successfully setup a project with d3.js!

## View your changes

In any text editor, open the file `js/main.js`. Look for this code at the bottom of the file:

```js
// Add each circle
database.circles.forEach(function(circle) {
        
    let radius = (circle.scale * scaleFactor) / 2;
    svg.append("circle")
        .attr("r", radius)
        .attr("cx", last_circle + radius)
        .attr("cy", height / 2)
        .attr("stroke", "none")
        .attr("fill", function() {
            switch (circle.group) {
            case 1:
                return "#ff0000"; // bright red
            case 2:
                return "#002fff"; // bright blue
            default:
                return "#000000"; // black
            }
        });
        
    last_circle += (padding + radius*2);
});
```

Change a color, for example, from red to yellow:

```js
.attr("fill", function() {
    switch (circle.group) {
    case 1:
        return "#ffdd00"; // bright yellow
```

Reload the page containing the five circles. You should see them change:

![html output](https://raw.githubusercontent.com/edahlgren/d3-test-setup/master/d3-changed-circles.png)

## View the SVG

To see the actual SVG, open the developer tools in your browser ([Firefox](https://developer.mozilla.org/en-US/docs/Tools), [Chrome](https://developers.google.com/web/tools/chrome-devtools)). From Chrome:

![chrome dev tools](https://raw.githubusercontent.com/edahlgren/d3-test-setup/master/d3-chrome-dev-tools.png)

Then under the "Elements" tab, expand the `<body>` tag, `<div>` tags, and `<svg>` tags. You should see the contents of the SVG:

![svg contents](https://raw.githubusercontent.com/edahlgren/d3-test-setup/master/d3-elements-svg.png)

Those are the basics!

