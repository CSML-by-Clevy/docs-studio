# Keywords

## goto

Inside a step, goto some other step. The step's memories are saved and its messages are sent right after this instruction, and before the next step is started.

Special cases:

* If the target step does not exist, the conversation will be closed.
* If the target step is `end`, the conversation is closed.

`goto` behaves as `return` in other languages: anything after a `goto` is ignored, the `goto` is immediately executed.

To reach another flow, you can also use `goto flow otherflow` .

```cpp
onestep:
  goto somestep
  say "after the goto" /* will not be executed */
  goto someotherstep /* will not be executed */

somestep:
  say "hi"

someotherstep: /* will not be executed */
  say "hey"
```

## if / else if / else

Simple logic operators `if`, `else if` and `else`. See examples.

```cpp
// regular notation
if (1 > 2) {
  say "I have my doubts"
} else if ("mi casa" == "tu casa") {
  say "Welcome home"
} else {
  say "The force is strong with you"
}

// shorthand notation
if (sky == "blue") goto beach
else goto restaurant
```

## say

Send a message to the end user.

```cpp
say "The quick brown fox jumps over the lazy dog."
```

## hold

Wait for user input: simply `hold` the conversation in place until the user responds.

```cpp
somestep:
  say "What's up doc?"
  hold

  remember updoc = event
  goto end
```

## match

Whether or not a variable "equals", in any way, another variable.

```cpp
use Button(
  title = "I agree",
  accept = ["OK", "yes", "right"]
) as btn

/* a direct click on the button will match the button */
/* typing "yes" will match the button */
/* typing "of course" will not match the button */
if (event match btn) {
  say "good"
} else {
  say "not good"
}
```

## remember

Save a value to the bot's memory with the given key. It can later be retrieved \(as soon as the next step\) with `"{{memory_item}}"`.

By default, the scope is bot/user/channel. The same user on a different channel, or a different user on the same channel, or the same user with a different bot will get a fresh memory instance.

```cpp
// remember a hardcoded value
remember truc = "tutu"

// remember a local variable
use 123 as myvar
remember tata = myvar

// overriding a local variable's scope
use 123 as myvar // `myvar` has a local scope
remember myvar = myvar // `myvar` is now a globally-available memory
use myvar as myvar // `myvar` will still be available globally
```

## do

Execute the following expression. Usually used for executing functions without caring for its return value, or for updating values of objects or arrays.

```cpp
// execute a function
do Fn("someFunc")

// assign new values
do array[3] = "X"
do obj.val.toto = 123

// however, this will fail:
remember myarr = [1, 2]
do myarr[42] = 1 // the array needs to have at least the requested number of items

remember myobj = Object("key"="value")
do myobj.missing.otherkey = 1 // all the parent properties must exist and be objects as well
```

## as

Save any value as a local variable, only available within the step. Local variables remain in memory after the step is done.

```cpp
do Button("A") as btn1
do Button("B") as btn2

// say and save a component at the same time
say Question(
  title = "Pick one",
  buttons = [btn1, btn2] as btnlist
) as myquestion

// repeat the same question
say myquestion
```

## use..as \(deprecated\)

See `as` keyword.

This keyword will be deprecated in a future release.

```cpp
use 42 as answer

say "The answer is {{answer}}"
```

## foreach

Iterate over each element of an array.

```cpp
use ["a", "b", "c"] as array
foreach (val, index) in array {
  say "at position {{index}} is element with value {{val}}"
}
```

## break

Exit from loops early and continue the flow execution normally.

```cpp
remember lightsabers = [
  {"color": "red", "owner": "Kylo Ren"},
  {"color": "purple", "owner": "Mace Windu"},
  {"color": "yellow", "owner": "Rey Skywalker"},
  {"color": "green", "owner": "Yoda"},
  {"color": "red", "owner": "Darth Vader"},
  {"color": "green", "owner": "Luke Skywalker"},
 ]

foreach ls in lightsabers {
  say "{{ls.owner}} had a {{ls.color}} lightsaber"
  // we want to stop after we find the first green lightsaber
  if (ls.color == "green") break
}

say "There might be even more lightsabers!"
```

## mathematical operators

In CSML, you can use the 4 basic mathematical operators `+`, `-`, `*` and `/`, as well as the modulo operator `%`. The regular order of operations applies.

