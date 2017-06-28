# Mathematical functions
Functional languages try to emulate mathematical functions.

## Terms
- Domain: The set of values can be used as input to the function
- Range: The set of values that can be possible output (technically the image on the codomain)
- Function: It maps the domain to the range
- immutability: Values can't change underneath you
- Pure function: A function which has a repeatable result and no side effects

## Key properties
- A function always gives the same output value for a given input value
- A function has no side effects.

```
Math function
Add1(x) = x+1

F# function
let add1 x = x + 1

Output from typing in the function
val add1 : int -> int
```
This means the function **add1** maps the domain **int** onto the range **int**
add1 is a **value**

### Pure functions
- Can easily parallelize
- I can use a function lazily, only evaluating it when I need the output. I can be sure that the answer will be the same whether I evaluate it now or later.
- I only ever need to evaluate a function once for a certain input, and I can then cache the result, because I know that the same input always gives the same output.
- If I have a number of pure functions, I can evaluate them in any order I like. Again, it can't make any difference to the final result.
  - Caching the results of functions is called "memoization"

### Unhelpful properties
How do you deal with a mathematical function having only 1 input and 1 output?

To do anything with a function that has multiple parameters you use currying
