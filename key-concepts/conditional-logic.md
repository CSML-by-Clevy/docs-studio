# Conditional Logic

As in any [turing-complete](https://en.wikipedia.org/wiki/Turing_completeness) programming language, CSML is able to handle any type of logic, in the form of loops and if/else statements.

As a CSML developer, you can easily implement any logic based on any variable or event, and very expressively decide how your conversation should be handled. Own of the main advantages of CSML is its descriptive textual interface, making it easy for anyone to understand the logic. It just makes sense and hides all the complexity of decision trees behind the simple concepts that every developer knows and uses.

A large part of developing CSML flows is about finding out whether an event matches a value in order to redirect the user to one step or another. The language comes with a number of helpers and operators:

* comparison operators `==`, `!=`, `<`, `>`, `<=`, `>=`
* `match` keyword
* `&&` and `||` operators
* `if`, `else if`, `else` keywords

```cpp
do btn = Button("yes")
do num = 1987
do batman = "Bruce Wayne"

if ("Hello!" match btn) say "Not at all"
if (54 < num) say "Absolutely true!"
if (3 >= 2 && batman != "Robin") say "Correct"
if (username match batman) say "I'm Batman"
```



