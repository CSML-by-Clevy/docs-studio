# Number methods

Although CSML differentiates between _Float_ and _Integer_, all methods are available on all Number types. Hence, the _Number_ type does not really exist but represents indifferently _Float_ and _Integer_.

Given the automatic type inference, CSML will automatically try to map integers and floats to whichever type makes more sense in the context.

### .pow\(Number\)

Raise the target integer to the power of the given integer.

```cpp
number.pow(Number) => Number

// example
do val = 3
do val.pow(2) // 9
```

### .abs\(\)

Return the absolute value of the target number.

```cpp
integer.abs() => Number

// example
do val = -42
do val.abs() // 42
```

### .cos\(\), .sin\(\), .tan\(\)

Return the cosine, sine or tangent of the target number.

```cpp
float.cos() => Float
float.sin() => Float

// example
do val = 12.34
do val.cos() // 0,9744873988
do val.sin() // -0,224442219
do val.tan() // -0,2303182363
```

### .floor\(\), .ceil\(\), .round\(\)

Round the number respectively down, up or using mathematical rounding.

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

### 

