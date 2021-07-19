# d3-polyBrush-v6

This is a compatible version of polybrush, created by Geoffrey T. Bell, for d3 v6.

This plugin is inspired by the d3-4.x based plugin from: [here](https://github.com/junwang23/polybrushv4).

Now the plugin can be instantiated like d3.brush() in [d3-6.x-api](https://github.com/d3/d3-brush).

```javascript
let brush = d3.polyBrush()
    .x({x_scale})
    .y({y_scale});

d3.select("svg")
    .append("g")
    .call(brush);
```

Please keep in mind that the ```extent``` in the polybrush is very different from that in d3-brush. So, the working area
of the brush can only be assigned by the ```range``` of the ```{x_scale}``` and ```{y_scale}```.

Three events are dispatched, which are ```start```, ```brush```, and ```end```, consistent with the events of d3-brush.
The event names are a bit different in the d3-3.x based version.

The rest is the same as using the d3-3.x version of the plugin.

```
Usage:
Click to add an anchor point, double click to close the selection.
Drag the selection to reposition it.
Double click outside the selection to clear it.
```

## Installing

Download d3-polyBrush-v6.js from this repository.

 ```html
<script src="d3-polyBrush-v6.js"></script>
<script>
    let brush = d3.polyBrush()
            .x(d3.scaleLinear().range([0, width]))
            .y(d3.scaleLinear().range([0, height]))
            .on("start", function () {
                // set the start callback function
            })
            .on("brush", function () {
               // set the brush callback function
            })
            .on('end', function () {
                // set the end callback function
            });
</script>
```

## API Reference

<a href="#polyBrush" name="polyBrush">#</a> d3.<b>polyBrush</b>()

Creates a new poly brush.

<a href="#brush_extent" name="brush_extent">#</a> <i>polyBrush</i>.<b>extent</b>() 

Returns the current extent.

<a href="#brush_x" name="brush_x">#</a> <i>polyBrush</i>.<b>x</b>([range])

If range is specified, sets the brushable x range to the specified scale.range(). If range is not specified, returns the current x range.

<a href="#brush_y" name="brush_y">#</a> <i>polyBrush</i>.<b>y</b>([range])

If range is specified, sets the brushable y range to the specified scale.range(). If range is not specified, returns the current y range.

<a href="#brush_isWithinExtent" name="brush_isWithinExtent">#</a> <i>polyBrush</i>.<b>isWithinExtent</b>(x, y)

Given the coordinates of an element, judge whether it is within the extent.

<a href="#brush_clear" name="brush_clear">#</a> <i>polyBrush</i>.<b>clear</b>()

Clear the extent and return the brush.

<a href="#brush_empty" name="brush_empty">#</a> <i>polyBrush</i>.<b>empty</b>()

Determine whether the extent is empty.

<a href="#brush_on" name="brush_on">#</a> <i>polyBrush</i>.<b>on</b>(<i>typenames</i>[, <i>listener</i>])

If *listener* is specified, sets the event *listener* for the specified *typenames* and returns the brush. If an event listener was already registered for the same type and name, the existing listener is removed before the new listener is added. If *listener* is null, removes the current event listeners for the specified *typenames*, if any. If *listener* is not specified, returns the first currently-assigned listener matching the specified *typenames*, if any. When a specified event is dispatched, each *listener* will be invoked with the same context and arguments as [*selection*.on](https://github.com/d3/d3-selection#selection_on) listeners: the current event `event` and datum `d`, with the `this` context as the current DOM element.

The *typenames* is a string containing one or more *typename* separated by whitespace. Each *typename* is a *type*, optionally followed by a period (`.`) and a *name*, such as `brush.foo` and `brush.bar`; the name allows multiple listeners to be registered for the same *type*. The *type* must be one of the following:

* `start` - at the start of a brush gesture, such as on mousedown.
* `brush` - when the brush moves, such as on mousemove.
* `end` - at the end of a brush gesture, such as on mouseup.

See [*dispatch*.on](https://github.com/d3/d3-dispatch#dispatch_on) and [Brush Events](#brush-events) for more.