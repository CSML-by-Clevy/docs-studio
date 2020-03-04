# Object methods

### .keys\(\)

```cpp
object.keys() => Array[String]

// example
do val = { "toto": 1, "tutu": 2 }
do val.keys() // ["toto", "tutu"]
```

Return the list of all 1st-level properties in the target object.

### .values\(\)

```cpp
object.values() => Array[String]

// example
do val = { "toto": 1, "tutu": 2 }
do val.values() // [1, 2]
```

Return the list of all 1st-level-property values in the target object.

### .remove\(String\)

```cpp
object.remove("property") => void

// example
do val = { "toto": 1, "tutu": 2 }
do val.remove("toto") // { "tutu": 2 }
```

Remove the given property from the target object.

### .length\(\)

```cpp
object.length() => Integer

// example
do val = { "toto": 1, "tutu": 2 }
do val.length() // 2
```

Return the number of 1st-level properties in the target object.

### 

