# Macros

### OneOf

Return one the elements of the array passed in the first argument at random.

Useful for randomisation of dialogue parts!

```cpp
say OneOf(["I like you", "You're awesome"])
```

### Shuffle

Given an array, return it with its elements in a random order.

Especially useful in questions to randomize the available options!

```cpp
use Button("Blue") as btn1
use Button("Red") as btn2
use Shuffle([btn1, btn2]) as btns

say Question(
  title = "Select a pill",
  buttons = btns
)
```

### Find

Return whether a string is contained in another string.

```cpp
say Find("needle", in="haystack") // false
say Find("yes", in="well yes, I like cheese") // true
```

### Length

Return the length of a given string or array

```cpp
say Length("My horse is amazing") // 19
say Length([1, 2, 3]) // 3
```

