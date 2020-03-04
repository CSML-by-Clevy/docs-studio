# Keywords

## goto

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

Inside a step, goto some other step. The step's memories are saved and its messages are sent right after this instruction, and before the next step is started.

Special cases:

* If the target step does not exist, the conversation will be closed.
* If the target step is `end`, the conversation is closed.

`goto` behaves as `return` in other languages: anything after a `goto` is ignored, the `goto` is immediately executed.

## if / else if / else

```cpp
if (1 > 2) {
  say "I have my doubts"
} else if ("mi casa" == "tu casa") {
  say "Welcome home"
} else {
  say "The force is strong with you"
}
```

> shorthand notation

```cpp
if (sky == "blue") goto beach
else goto restaurant
```

Simple logic operators `if`, `else if` and `else`. See examples.

## say

```cpp
say "The quick brown fox jumps over the lazy dog."
```

Send a message to the end user.

## hold

```cpp
somestep:
  say "What's up doc?"
  hold

  remember updoc = event
  goto end
```

Wait for user input: simply `hold` the conversation in place until the user responds.

## match

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

Whether or not a variable "equals", in any way, another variable.

## remember..as

> remember a hardcoded value

```cpp
remember truc = "tutu"
```

> remember a local variable

```cpp
use 123 as myvar
remember tata = myvar
```

> overriding a local variable's scope

```cpp
use 123 as myvar // `myvar` has a local scope
remember myvar = myvar // `myvar` is now a globally-available memory
use myvar as myvar // `myvar` will still be available globally
```

Save a value to the bot's memory with the given key. It can later be retrieved \(as soon as the next step\) with `"{{memory_item}}"`.

By default, the scope is bot/user/channel. The same user on a different channel, or a different user on the same channel, or the same user with a different bot will get a fresh memory instance.

## use..as

```cpp
use Button("A") as btn1
use Button("B") as btn2

/* say and save a component at the same time */
say Question(
  title = "Pick one",
  buttons = [btn1, btn2] as btnlist
) as myquestion

/* repeat the same question */
say myquestion
```

Save something as a locally-available variable \(within a step\). Does not remain in memory after the step is done.

In shorthand notation, the \`use\` keyword is not always necessary \(for example when inside a function declaration or when a say instruction is used\).

## foreach

```cpp
use ["a", "b", "c"] as array
foreach (val, index) in array {
  say "at position {{index}} is element with value {{val}}"
}
```

Iterate over each element of an array.

## break

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

Exit from loops early and continue the flow execution normally.

## do

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

Execute the following expression. Usually used for executing functions without caring for its return value, or for updating values of objects or arrays.

## mathematical operators

In CSML, you can use the 4 basic mathematical operators `+`, `-`, `*` and `/`, as well as the modulo operator `%`. The regular order of operations applies.

