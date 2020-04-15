# Automatic Type Inference

All incoming events are theoretically strings.

The reason is simple: there is no way for a chat client to differenciate between for example a `number` type and a `string` type as this was typed into an input field or spoken to a voice interface.

However, the language must have a way to perform arithmetic operations anyway. 

At the same time, any external function used in the program can return any arbitrary JSON-like object representation, or string, or any type of value.

To handle all these cases at runtime, the CSML interpreter will automatically detect the type of any variable and try to make the best decision depending on how you want to use it. This process is called type inference.

The example below shows how it works for numbers.

```cpp
/* event = "42" */

guessthenumber:
  say "pick a number!"
  hold

  /* compare the input with an arbitrary target number */
  if (event > 57) {
    say "Too high!"
    goto guessthenumber
  }
  else if (event < 57) {
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



