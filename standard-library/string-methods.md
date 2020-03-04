# String methods

### Strings

You can find more info about the particular regex syntax used in the `*_regex` methods on [this link](https://docs.rs/regex/1.3.4/regex/#syntax).

#### .to\_uppercase\(\)

```cpp
string.to_uppercase() => String

// example
do val = "Where is Brian?"
do val.to_uppercase() // "WHERE IS BRIAN?"
```

Return the same string in all uppercase characters.

#### .to\_lowercase\(\)

```cpp
string.to_lowercase() => String

// example
do val = "Where is Brian?"
do val.to_lowercase() // "where is brian?"
```

Return the same string in all lowercase characters.

#### .length\(\)

```cpp
string.length() => Integer

// example
do val = "Where is Brian?"
do val.length() // 15
```

Return the length of the target string.

#### .contains\(String\), .contains\_regex\(String\)

```cpp
haystack.contains(needle) => Boolean
haystack.contains_regex(needle) => Boolean

// example
do val = "Where is Brian?"
// does it contain any "r"?
do val.contains("r") // true
// does it contain the word "where"?
do val.contains("where") // false => no, because it is case sensitive
// does it contain any number?
do val.contains_regex("[0-9]") // true
```

Return whether the string contains another string or expression.

#### .starts\_with\(String\), .starts\_with\_regex\(String\)

```cpp
haystack.starts_with(needle) => Boolean
haystack.starts_with_regex(needle) => Boolean

// example
do val = "Where is Brian?"
// does it start with "r"?
do val.starts_with("r") // false
// does it start with any uppercase letter?
do val.starts_with_regex("[A-Z]") // true
```

Return whether a string starts with another string or expression.

#### .ends\_with\(String\), .ends\_with\_regex\(String\)

```cpp
haystack.ends_with(needle) => Boolean
haystack.ends_with_regex(needle) => Boolean

// example
do val = "Where is Brian?"
// does it end with "r"?
do val.ends_with("r") // false
// does it end with any uppercase letter?
do val.ends_with_regex("[A-Z]") // false
```

Return whether a string ends with another string or expression.

#### .match\(String\), .match\_regex\(String\)

```cpp
haystack.match(needle) => Array[String]
haystack.match_regex(needle) => Array[String]

// example
do val = "Where is Brian?"
// does it match with "r"?
do val.match("r") // ["r", "r"] => yes, twice!
// does it match with any uppercase letter?
do val.match_regex("[A-Z]") // ["W", "B"] => yes, and these are the letters!
```

Return all the matches of the string or expression in the target string, or Null if none are found.

### Arrays

#### .length\(\)

```cpp
array.length() => Integer

// example
do val = ["Batman", "Robin", "Superman"]
do val.length() // 3
```

Return the number of elements contained in the target array.

#### .push\(\*\)

```cpp
array.push(val) => void

// example
do val = ["Batman", "Superman"]
do val.push("Robin") // ["Batman", "Superman", "Robin"]
```

Add an element at the end of an array.

#### .pop\(\)

```cpp
array.pop() => void

// example
do val = ["Batman", "Robin", "Superman"]
do val.pop() // ["Batman", "Robin"]
```

Remove the last element of an array.

#### .insert\_at\(Integer, \*\)

```cpp
array.insert_at(n, val) => void

// example
do val = ["Batman", "Superman"]
do val.insert_at(1, "Robin") // ["Batman", "Robin", "Superman"]
```

Add an element at position n of an array \(shifting the position of all the following elements\).

#### .remove\_at\(Integer\)

```cpp
array.remove_at(n) => void

// example
do val = ["Batman", "Robin", "Superman"]
do val.remove_at(1) // ["Batman", "Superman"]
```

Remove the nth element of an array \(unshifting the position of all the following elements\).

### Objects

#### .keys\(\)

```cpp
object.keys() => Array[String]

// example
do val = { "toto": 1, "tutu": 2 }
do val.keys() // ["toto", "tutu"]
```

Return the list of all 1st-level properties in the target object.

#### .values\(\)

```cpp
object.values() => Array[String]

// example
do val = { "toto": 1, "tutu": 2 }
do val.values() // [1, 2]
```

Return the list of all 1st-level-property values in the target object.

#### .remove\(String\)

```cpp
object.remove("property") => void

// example
do val = { "toto": 1, "tutu": 2 }
do val.remove("toto") // { "tutu": 2 }
```

Remove the given property from the target object.

#### .length\(\)

```cpp
object.length() => Integer

// example
do val = { "toto": 1, "tutu": 2 }
do val.length() // 2
```

Return the number of 1st-level properties in the target object.

### Integers

#### .pow\(Integer\)

```cpp
integer.pow(Integer) => Integer

// example
do val = 3
do val.pow(2) // 9
```

Raise the target integer to the power of the given integer.

#### .abs\(\)

```cpp
integer.abs() => Integer

// example
do val = -42
do val.abs() // 42
```

Return the absolute value of the target number.

### Floats

#### .pow\(Float\)

```cpp
float.pow(Float) => Integer

// example
do val = 3.5
do val.pow(2.8) // 5.994747701113033
```

Raise the target integer to the power of the given integer.

#### .abs\(\)

```cpp
float.abs() => Integer

// example
do val = -42.42
do val.abs() // 42.42
```

Return the absolute value of the target number.

#### .cos\(\), .sin\(\)

```cpp
float.cos() => Float
float.sin() => Float

// example
do val = 12.34
do val.cos() // 0.9744873987650982
do val.sin() // 0.9744873987650982
```

Return the cosine or sine of the target number.

#### .floor\(\), .ceil\(\), .round\(\)

```cpp
float.floor() => Integer
float.ceil() => Integer
float.round() => Integer

// example
do val = 10.5
do val.floor() // 10
do val.ceil() // 11
do val.round() // 11
```

Round the number respectively down, up or using mathematical rounding.

### 

