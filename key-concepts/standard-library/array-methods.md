# Array methods

### .length\(\)

Return the number of elements contained in the target array.

```cpp
array.length() => Integer

// example
do val = ["Batman", "Robin", "Superman"]
do val.length() // 3
```

### .push\(\*\)

Add an element at the end of an array.

```cpp
array.push(val) => void

// example
do val = ["Batman", "Superman"]
do val.push("Robin") // ["Batman", "Superman", "Robin"]
```

### .pop\(\)

Remove the last element of an array.

```cpp
array.pop() => void

// example
do val = ["Batman", "Robin", "Superman"]
do val.pop() // ["Batman", "Robin"]
```

### .insert\_at\(Integer, \*\)

Add an element at position n of an array \(shifting the position of all the following elements\).

```cpp
array.insert_at(n, val) => void

// example
do val = ["Batman", "Superman"]
do val.insert_at(1, "Robin") // ["Batman", "Robin", "Superman"]
```

### .remove\_at\(Integer\)

Remove the nth element of an array \(unshifting the position of all the following elements\).

```cpp
array.remove_at(n) => void

// example
do val = ["Batman", "Robin", "Superman"]
do val.remove_at(1) // ["Batman", "Superman"]
```

### .find\(\*\)

Returns a new array with all the values found in the original array matching the given value.

```cpp
array.find(x) => void

// example
do val = ["Batman", "Robin", "Superman", "Batman"]
do val.find("Ironman") // []
do val.find("Robin") // ["Robin"]
do val.find("Batman") // ["Batman", "Batman"]
```

