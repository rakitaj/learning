# How types work with functions
## Understanding the type notation

In a function signature the arrow notation -> shows the domain and range.
Example functions
```fsharp
let intToString x = sprintf "x is %i" x  // format int to string
let stringToInt x = System.Int32.Parse(x)
```
Example signatures of those functions when evaluated
```fhsarp
val intToString : int -> string
val stringToInt : string -> int
```

## Primative types
The primative types are from the .Net type system.

## Type annotations
```fsharp
let stringLength (x:string) = x.Length
```
The parens are important, otherwise it will think string is the return value. A colon ':' without parens is used to denote the return value.
```fsharp
// Parameter type of string, return type of int
let stringLengthAsInt (x:string) :int = x.Length     
```

## Function types as parameters
A function which takes other functions as parameters, or returns a function is called a **higher-order function**

## Using type annotations to constrain function types
Can add function type parameters

## The "unit" type
It's like the void type in C#, except it's a real value. It's used when the function doesn't return anything.
It is '()'

## Generic types
In F# I don't declare a generic type, it just works. In the signature the parameter has an apostrophe in front.
```fsharp
let onAStick x = x.ToString() + " on a stick"
// Signature is
val onAStick : 'a -> string
```

In C# it would be
```csharp
string onAStick<a>();
// Or more idiomatically
string onAStick<TObject>();
```

## Other types
- Tuples - A pair, triple, or more of other types
- Collection types - lists, sequences, arrays
- Option type - Two cases, Some and None
- Discriminated union - Built from a set of other types
- Record - like structs or database rows, a list of named slots

## Test your understanding of types
```fsharp
let testA   = float 2
// val testA : float = 2
let testB x = float 2
// val testB : float = 2
// val testB : x:'a -> float
let testC x = float 2 + x
// val testC : x:float -> float
let testD x = x.ToString().Length
// val testD : x:'a -> int
let testE (x:float) = x.ToString().Length
// val testE : x:float -> int
let testF x = printfn "%s" x
// val testF : x:string -> unit
let testG x = printfn "%f" x
// val testG : x:float -> unit
let testH   = 2 * 2 |> ignore
// val testH : int = 4
// val testH : unit = ()
let testI x = 2 * 2 |> ignore
// val testI : x:unit -> unit
// val testI : x:'a -> unit
let testJ (x:int) = 2 * 2 |> ignore
// val testJ : x:'a -> unit
// val testJ : x:int -> unit
let testK   = "hello"
// val testK : string = "hello" 
let testL() = "hello"
// val testL : unit -> string
let testM x = x=x
// val testM : x:'a -> bool
// val testM : x:'a -> bool when 'a : equality
let testN x = x 1          // hint: what kind of thing is x?
// val testN : (int -> x:'a) -> x:'a
// val testN : x:(int -> 'a) -> 'a
let testO x:string = x 1   // hint: what does :string modify? 
// val testO : x:(int -> string) -> string