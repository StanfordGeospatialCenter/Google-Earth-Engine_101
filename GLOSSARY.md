# Glossary (Earth Engine context)

Below are short, Earth Engine–focused definitions of common JavaScript and
Earth Engine concepts you'll see in the tutorials.

## arrays (list)

In JavaScript an array is a zero-indexed list: `['a', 'b', 'c']`. In Earth
Engine you will encounter both client-side JavaScript arrays (plain JS arrays)
and server-side `ee.List` objects. Use plain arrays for local operations and
`ee.List` when you need to build or manipulate data on the Earth Engine server.

Example (client-side array):

```javascript
var colors = ['red', 'green', 'blue'];
print(colors[0]); // 'red' (immediate, client-side)
```

Example (server-side ee.List):

```javascript
var eeList = ee.List(['red', 'green', 'blue']);
print(eeList.get(0)); // returns a server-side value that the Code Editor shows
```

## function

A reusable block of code. In Earth Engine JavaScript you'll use functions for
local computation and as callbacks passed to server-side methods such as
`ImageCollection.map()` or `FeatureCollection.map()`. Functions that are used
as mapping callbacks are serialized and executed on the Earth Engine server,
so they must return `ee.*` objects when operating on server-side inputs.

Example (mapping an ImageCollection):

```javascript
var addNDBI = function(image) {
  var ndbi = image.normalizedDifference(['B5', 'B4']).rename('NDBI');
  return image.addBands(ndbi);
};

var withNDBI = collection.map(addNDBI);
```

## javascript

The programming language used in the Earth Engine Code Editor. Most standard
JavaScript syntax applies (variables, functions, arrays, objects), but Earth
Engine adds the `ee` namespace (e.g., `ee.Image`, `ee.List`) for server-side
data structures. The Code Editor environment differs from a browser: there is
no DOM, and many operations build a computation graph that runs on Google's
servers rather than executing immediately in your local JS runtime.

## object (dictionary)

In plain JavaScript an object (often called a dictionary) is a set of key-value
pairs enclosed in `{}` (for example: `{a: 1, b: 2}`). Earth Engine provides a
server-side `ee.Dictionary` for similar key-value storage on the server. Use
`ee.Dictionary.get()` and related methods to access values server-side.

Example (client-side object):

```javascript
var props = {name: 'lake', area_km2: 12.5};
print(props.name);
```

Example (server-side ee.Dictionary):

```javascript
var d = ee.Dictionary({name: 'lake', area_km2: 12.5});
print(d.get('area_km2'));
```

## variable

A named reference to a value. In Earth Engine scripts variables often hold
references to `ee` objects such as `ee.Image`, `ee.ImageCollection`, or
`ee.FeatureCollection`. Remember that many `ee` objects are immutable: most
operations return new objects rather than modifying the original.

Examples:

```javascript
var img = ee.Image('LANDSAT/LC08/C01/T1_SR/LC08_044034_20140318');
var clipped = img.clip(geometry); // returns a new ee.Image
```

Note on client vs server values: a variable can reference either a local
JavaScript value (number, string, JS array) or a server-side `ee.*` object.
To view server-side contents in the Code Editor use `print()` or export
operations; attempting to treat `ee.*` objects like plain JS values can lead
to errors.

