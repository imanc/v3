The ability for something to be defined in terms of itself is called recursion. In F#, recursion is most commonly found in recursive functions, which are functions that call themselves. A recursive function is defined like a regular function, but with the `rec` modifier. Without this modifier, a function will _not_ be able to call itself and any attempt to do so will result in a compilation error. Recursion thus has to be explicitly opted into.

One possible issue with recursive functions is that each (recursive) function call results in allocations on the stack, causing it to grow. As the stack has a limited amount of memory, functions that use many recursive calls may cause a `StackOverflowException` to be thrown. How many recursive calls will trigger this behavior depends on multiple factors, like the available memory on the stack and how much data each function call takes up on the stack.

The best way to prevent recursive functions from overflowing the stack is to write them as _tail-recursive_ functions. When a function is tail-recursive, the compiler can optimize its output such that there are no additional allocations on the stack for each recursive function call. The one rule for tail-recursive functions is that the result of a recursive function call should be directly returned from the function, there must not be any additional code that processes the result of the recursive call. The most common way to do this is by creating a helper function that takes an additional accumulator argument, which is updated for each recursive call and returned when the recursion finishes.

F# also supports recursive types through discriminated union types. A recursive discriminated union type has one or more of its cases refer to the discriminated union type itself in their data.

Lists in F# can be considered as a recursive type, with a list being either an empty list or having a head element followed by a list. It is usually not necessary to manually write recursive functions to process lists, as the most commonly used (recursive) list processing patterns have built-in functions defined for them. If you do find you need to process a list manually, you can use pattern matching to do so recursively. The pattern is quite simple: if the list matches the empty list pattern, the recursive processing ends and a value is returned. If the list is not empty, it will match the non-empty list pattern, which is usually defined as matching the first (head) element and a remainder. The head element is processed and the remainder is processed recursively.