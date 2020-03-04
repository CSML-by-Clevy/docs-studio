# Automatic Type Inference

CSML is dynamically typed \(even though it was written in Rust, a strong-typed, memory-safe, low-level language\). The reason is simple: there is no way for a chat client to differenciate between a `number` type and a `string` type, but the language must have a way to perform arithmetic operations anyway. Also, any external function used in the program can return any arbitrary JSON-like object representation, or string, or any type of value.

To handle all these cases at runtime, the CSML interpreter will automatically detect the type of any variable and try to make the best decision depending on how you want to use it.

```cpp
/* event = "42" */

guessthenumber:
  say "pick a number!"
  hold

  /* compare the input with an arbitrary target number */
  if (event > 57) {
    say "Too high!"
    goto guessthenumber
  } else if (event < 57) {
    say "Too low!"
    goto guessthenumber
  }
  /* use the number as a string as well */
  else {
    say event
    say "You are right, {{event}} is the right number!"
    goto end
  }
```



