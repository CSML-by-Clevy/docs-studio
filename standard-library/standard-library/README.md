# Standard Library

CSML exposes a number of built-in functions and macros that make many operations easier. They are what you could call the `stdlib` of CSML. The number of builtins will grow as the need arises: you can expect some new builtins as part of the upcoming features! All builtins are synchronous, by the way.

You can absolutely nest functions within functions. The innermost function will return and make its result as a parameter of the calling function, recursively.

You can also chain methods based on their return value using dot notation:`somevar.method1().method2()`.

### 

