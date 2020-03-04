# Literals, Objects, Arrays

CSML is able to natively understand literal types \(`int`, `float`, `string`, ...\) as well as more complex types such as JSON-like objects and arrays.

The CSML interpreter will automatically parse the object with the usual dot notation `x.y.z` and detect the type of the resulting property. If one of the properties in the chain does not exist or is not an object itself, it will evaluate to `NULL`.

## Objects

You can create an object by returning a JSON-like object from any function, or directly in the CSML code with the `Object()` helper function or by using a shorthand notation similar to JSON format.

```cpp
// Object representation
use Object(
  title = "toto",
  body = Object(
    somekey = "somevalue",
    otherkey = 123
  )
) as obj1


// Shorthand notation
use { 
  "title": "toto",
  "body": { 
    "somekey": "somevalue", 
    "otherkey": 123
  }
} as obj2

say obj1.title // "toto"
say obj2.body.otherkey // 123
```

## Arrays

You can also iterate over an array \(represented by items inside square brackets: `["a", "b", "c"]`\) with the `foreach` keyword, and access any of its items by using its index in square brackets notation: `items[2]`.

```cpp
// Arrays
use ["a", "b", "c"] as items

/* iterate over all the elements in the array */
foreach (elem, index) in items {
  say "index: {{index}}, elem: {{elem}}"
}

say items[2] /* "c" */
```

Finally, you can also modify the contents of an array either by assigning a new value to any of the items in the array, adding new items at the end with `array.push(elem)` or removing the last element with `array.pop()`.

```cpp
// Array operations
use ["a", "b", "c"] as items

do items.pop() // ["a", "b"]
do items.push("x") // ["a", "b", "x"]
do items[1] = "Z" // ["a", "Z", "x"]
```

## Printing non-literal values

To print any value as a string, simply use the `Text(value)` component or use the curly-brace template syntax `"{{value}}"`

