# Function Values and Simple Values
The simple function
```
let add1 x = x + 1
```
## About the function
- x is bound to the input value
- **binding is not assignment**, x is not a slot or variable this is assigned to the value and can be assigned to another value.
- **add1** is a function value, it tells the compiler that everytime it sees add1 to replace with with the adding 1 function

## Function values
A function value always has the signature
```
val functionName: domain -> range
```

## Simple values
```fsharp
Enter
let c = 5
Evaluated
val c : int = 5
// Simple values always have a signature like
val aName: type = constant
```

Functions are values that can be passed around as inputs to other functions 

### Constant function
```fsharp
let c = fun() -> 5
let c() = 5
// Signature is
val c : unit -> int
```

## Values vs Objects
A value is just a member of a domain. Values are immutable and don't have behavior associated/attached to them.

## Naming values
Apostrophes ' are ok!?! They can be used anywhere except the first character.
```fsharp
let f = x
let f' = derivative f
let f'' = derivative f'
```
Double backticks made anythign a valid identifier
```fsharp
let `like this works!` = true
```

functions and values start with a lowercase letter, unlike C#
Types and Modules start with an uppercase letter