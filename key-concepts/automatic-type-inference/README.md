# Value Types

CSML is a dynamically-typed language, even though it is written in Rust, a strong-typed, memory-safe, low-level language. It can handle a lot of different types but some magic happens behind the scenes to make it as easy for the developers to use the language.

In this section, let's learn more about how CSML handles the various quirks a chatbot needs to solve!

```cpp
do number = 3
do string = "something"
do float = -4.7
do object = { "hey": "you" }
do array = [1, 2, number]
do boolean = true
```

