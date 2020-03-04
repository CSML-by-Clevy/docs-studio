# Interpolation

To output the value of any variable in a string, you can use the string interpolation helper: double curly braces `{{ }}`.

This makes it extremely easy to concatenate multiple values of any type into a single string. Objects, arrays and numbers will be stringified automatically and missing properties will be evaluated as `NULL`.

```cpp
start:
  say "Hi! My name is {{what}}"
  say "My name is {{who}}"
  say "My name is {{slim_shady}}"

// Which is the same as:
start:
  say "Hi! My name is {{eminem.what}}"
  say "My name is {{eminem.who}}"
  say "My name is {{eminem.slim_shady}}"

// Alternatively, the following syntax is possible too, but will result in only one text bubble:
start:
  say "Hi! My name is {{what}}. My name is {{who}}. My name is {{slim_shady}}"
```

