Polymer Flot Element
====================

This is a (simplified) [polimerization](https://www.polymer-project.org/) of the [Flot](http://www.flotcharts.org/) plotting libarary for jQuery.

## Elements

The `flot-chart` element has `data` and `options` attributes that it forwards to Flot's `$.plot()` function. You can refer to Flot's documentation for the [data format](https://github.com/flot/flot/blob/master/API.md#data-format) and [plot options](https://github.com/flot/flot/blob/master/API.md#plot-options).

## Usage

Import ...

```html
<link rel="import" href="bower_components/polymer-flot/flot-chart.html">
```

... use ...

```html
<flot-chart id="some_chart" data="[ [[0, 3], [4, 8], [8, 5], [9, 13]] ]"></flot-chart>
```

... and update via JavaScript.

```javascript
var some_series = [];
for (var i = 0; i < 14; i += 0.5) {
  some_series.push([i, Math.sin(i)]);
}

$("#some_chart").prop('data', [some_series]);
```

## Caveats

Polymer won't recognize changes (e.g. to data series) if you change the data inplace and the data array (object) stays the same.

```javascript
var some_series = [/*point1, point2, ...*/];
var some_data = [some_series];
$("#some_chart").prop('data', some_data);

// ... later

// update the series, but no changes to the data array
some_series.push([/*new, point*/]);
$("#some_chart").prop('data', some_data);
// this won't update the chart since some_data is still the same
```

Doing a [shallow copy](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) of the data array will make it work again.

```javascript
$("#some_chart").prop('data', some_data.slice());
```
