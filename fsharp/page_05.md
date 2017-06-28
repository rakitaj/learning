# Currying
## Breaking multi-parameter functions into smaller one-parameter functions

```fsharp
//normal version
let printTwoParameters x y = printfn "x=%i y=%i" x y
//explicitly curried version
let printTwoParameters x  =    // only one parameter!
   let subFunction y = printfn "x=%i y=%i" x y  // new function with one param
   subFunction                 // return the subfunction
```

