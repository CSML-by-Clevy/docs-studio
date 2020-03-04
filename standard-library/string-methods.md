# String methods

You can find more info about the particular regex syntax used in the `*_regex` methods on [this link](https://docs.rs/regex/1.3.4/regex/#syntax).

### .to\_uppercase\(\)

Return the same string in all uppercase characters.

```cpp
string.to_uppercase() => String

// example
do val = "Where is Brian?"
do val.to_uppercase() // "WHERE IS BRIAN?"
```

### .to\_lowercase\(\)

Return the same string in all lowercase characters.

```cpp
string.to_lowercase() => String

// example
do val = "Where is Brian?"
do val.to_lowercase() // "where is brian?"
```

### .length\(\)

Return the length of the target string.

```cpp
string.length() => Integer

// example
do val = "Where is Brian?"
do val.length() // 15
```

### .contains\(String\), .contains\_regex\(String\)

Return whether the string contains another string or expression.

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

### .starts\_with\(String\), .starts\_with\_regex\(String\)

Return whether a string starts with another string or expression.

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

### .ends\_with\(String\), .ends\_with\_regex\(String\)

Return whether a string ends with another string or expression.

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

### .match\(String\), .match\_regex\(String\)

Return all the matches of the string or expression in the target string, or Null if none are found.

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

### .is\_number\(\)

Return whether the given string represents a numerical value.

```cpp
string.is_number() => Boolean

// example
do val = "Where is Brian?"
do val.is_number() // false

do val = "42"
do val.is_number() // true
```

