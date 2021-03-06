**Fabric.js** is a framework that makes it easy to work with HTML5 canvas element. It is an **interactive object model** on top of canvas element. It is also an **SVG-to-canvas parser**. 

Using Fabric.js, you can create and populate objects on canvas; objects like simple geometrical shapes — rectangles, circles, ellipses, polygons, or more complex shapes consisting of hundreds or thousands of simple paths. You can then scale, move, and rotate these objects with the mouse; modify their properties — color, transparency, z-index, etc. You can also manipulate these objects altogether — grouping them with a simple mouse selection.

### Goals

- Unit tested (939 tests at the moment)
- Modular (~20 small "classes")
- Cross-browser
- Fast
- Encapsulated in one object
- No browser sniffing for critical functionality

### Supported browsers

- Firefox 2+
- Safari 3+
- Opera 9.64+
- Chrome 1+
- IE9 PP4

#### With help of [Explorer Canvas](http://code.google.com/p/explorercanvas/)

- IE8 (incomplete — about 17 failing tests at the moment)
- IE7,6 (incomplete - about 27 failing tests at the moment)

### History

Fabric.js started as a foundation for design editor on [printio.ru](http://printio.ru) — interactive online store with ability to create your own designs. The idea was to create [Javascript-based editor](http://printio.ru/ringer_man_tees/new), which would make it easy to manipulate vector shapes and images on T-Shirts. Since performance was one of the most critical requirements, we chose canvas over SVG. While SVG is excellent with static shapes, it's not as performant as canvas when it comes to dynamic manipulation of objects (movement, scaling, rotation, etc.). Fabric.js was heavily inspired by [Ernest Delgado's canvas experiment](http://www.ernestdelgado.com/public-tests/canvasphoto/demo/canvas.html). In fact, code from Ernest's experiment was the foundation of an entire framework. Later, Fabric.js grew into a collection of distinct object types and got an SVG-to-canvas parser.

### Building

1. Install [Sprockets](http://github.com/sstephenson/sprockets)

        $ gem install --remote sprockets

2. Build distribution file

        $ sprocketize fabric.js > dist/all.js

3. Create a minified distribution file

        # Using YUICompressor
        $ java -jar lib/yuicompressor-2.4.2.jar dist/all.js -o dist/all.min.js
        
        # or Google Closure Compiler
        $ java -jar lib/google_closure_compiler.jar --js dist/all.js --js_output_file dist/all.min.js

### Demos

- [Main demo](http://yura.thinkweb2.com/canvas_demo/test/demo/)
- [Benchmark (quantity)](http://yura.thinkweb2.com/canvas_demo/test/benchmarks/quantity.html)
- [Benchmark (animation)](http://yura.thinkweb2.com/canvas_demo/test/benchmarks/animation.html)

### Examples of use

#### Adding red rectangle to canvas
  
    <canvas id="canvas" width="300" height="300"></canvas>  
    ...
    
    var canvas = new fabric.Element('canvas');
    
    var rect = new fabric.Rect({
      top: 100,
      left: 100,
      width: 60,
      height: 70,
      fill: 'red'
    });
    
    canvas.add(rect);

### Object Model hierarchy
    
      fabric.Object
        |
        -- fabric.Line
        |
        -- fabric.Circle
        |
        -- fabric.Triangle
        |
        -- fabric.Ellipse
        |
        -- fabric.Rect
        |
        -- fabric.Polyline
        |
        -- fabric.Polygon
        |
        -- fabric.Group
        |
        -- fabric.Text
        |
        -- fabric.Image
        |
        -- fabric.Path
             |
             -- fabric.PathGroup
      
      
      fabric.util
        |
        -- removeFromArray
        |
        -- degreesToRadians
        |
        -- toFixed
        |
        -- getRandomInt
    
      
      Canvas
        |
        -- parseAttributes
        |
        -- parseElements
        |
        -- parseStyleAttribute
        |
        -- parsePointsAttribute
      
      
      fabric.Element

      fabric.Point

      fabric.Intersection

      fabric.Color

### Credits

- Ernest Delgado for the original idea of [manipulating images on canvas](http://www.ernestdelgado.com/archive/canvas/).
- [Maxim "hakunin" Chernyak](http://twitter.com/hakunin) for ideas, and help with various parts of the library.
- [Sergey Nisnevich](http://nisnya.com) for help with geometry logic.

### MIT License

Copyright (c) 2008-2010 Bitsonnet

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

### TODO

- All methods under fabric.util.* (except misc.js) need unit tests
- SVG-to-canvas parser needs to support more SVG declarations (e.g. gradients are not yet supported)