Polymer Flot Element
====================

This is a (simplified) polimerization of the [Flot](http://www.flotcharts.org/) plotting libarary for jQuery.

## Elements

The `flot-chart` element has `data` and `options` attributes that it forwards to Flot's `$.plot()` function. You can refer to Flot's documentation for the [data format](https://github.com/flot/flot/blob/master/API.md#data-format) and [plot options](https://github.com/flot/flot/blob/master/API.md#plot-options).

## Usage

Somewhere in your HTML:
```html
<flot-chart id="chart" />
```

Then set the data from JavaScript:
```javascript
var some_data = [];
for (var i = 0; i < 14; i += 0.5) {
  some_data.push([i, Math.sin(i)]);
}

// use ANY of the following calls to update the chart
$("#chart").prop('data', [some_data]);
$("#chart")[0].data = [some_data];
document.getElementById("chart").data = some_data;
```
