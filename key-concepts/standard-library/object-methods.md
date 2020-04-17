# Object methods

### .keys\(\)

Return the list of all 1st-level properties in the target object.

```cpp
object.keys() => Array[String]

// example
do val = { "toto": 1, "tutu": 2 }
do val.keys() // ["toto", "tutu"]
```

### .values\(\)

Return the list of all 1st-level-property values in the target object.

```cpp
object.values() => Array[String]

// example
do val = { "toto": 1, "tutu": 2 }
do val.values() // [1, 2]
```

### .remove\(String\)

Remove the given property from the target object.

```cpp
object.remove("property") => void

// example
do val = { "toto": 1, "tutu": 2 }
do val.remove("toto") // { "tutu": 2 }
```

### .length\(\)

Return the number of 1st-level properties in the target object.

```cpp
object.length() => Integer

// example
do val = { "toto": 1, "tutu": 2 }
do val.length() // 2
```

### 

