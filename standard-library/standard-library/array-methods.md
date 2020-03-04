# Array methods

### .length\(\)

```cpp
array.length() => Integer

// example
do val = ["Batman", "Robin", "Superman"]
do val.length() // 3
```

Return the number of elements contained in the target array.

### .push\(\*\)

```cpp
array.push(val) => void

// example
do val = ["Batman", "Superman"]
do val.push("Robin") // ["Batman", "Superman", "Robin"]
```

Add an element at the end of an array.

### .pop\(\)

```cpp
array.pop() => void

// example
do val = ["Batman", "Robin", "Superman"]
do val.pop() // ["Batman", "Robin"]
```

Remove the last element of an array.

### .insert\_at\(Integer, \*\)

```cpp
array.insert_at(n, val) => void

// example
do val = ["Batman", "Superman"]
do val.insert_at(1, "Robin") // ["Batman", "Robin", "Superman"]
```

Add an element at position n of an array \(shifting the position of all the following elements\).

### .remove\_at\(Integer\)

```cpp
array.remove_at(n) => void

// example
do val = ["Batman", "Robin", "Superman"]
do val.remove_at(1) // ["Batman", "Superman"]
```

Remove the nth element of an array \(unshifting the position of all the following elements\).

