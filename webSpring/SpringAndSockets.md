#  Spring and Sockets
*In computer science, purely functional programming usually designates a programming paradigm—a style of building the structure and elements of
computer programs—that treats all computation as the evaluation of mathematical functions.*

*Program state and mutable objects are usually modeled with temporal logic, as explicit variables that represent the program state at each step of a program
execution: a variable state is passed as an input parameter of a state-transforming function,
which returns the updated state as part of its return value. This style handle state changes without losing the referential transparency of the program expressions.*

*Purely functional programming consists of ensuring that functions, inside the functional paradigm, will only depend on their arguments, regardless of any global or
local state. A pure functional subroutine only has visibility of changes of state represented by state variables included in its scope.*

### Programming paradigms

*are a way to classify programming languages based on their features. Languages can be classified into multiple paradigms.*

### Program state

*In information technology and computer science, a system is described as stateful if it is designed to remember preceding events or user interactions;
the remembered information is called the state of the system.*

## Difference between pure and impure functional programming

*he exact difference between pure and impure functional programming is a matter of controversy.*

*A program is usually said to be functional when it uses some concepts of functional programming, such as first-class functions and higher-order functions.
However, a first-class function need not be purely functional, as it may use techniques from the imperative paradigm, such as arrays or input/output methods 
that use mutable cells, which update their state as side effects. In fact, the earliest programming languages cited as being functional, IPL and Lisp
were both "impure" functional languages by the current definition.*

*Purely functional data structures are persistent. Persistency is required for functional programming; without it, the same computation could return different results. 
Functional programming may use persistent non-purely functional data structures, while those data structures may not be used in purely functional programs.*


## Strict versus non-strict evaluation

Each evaluation strategy which ends on a purely functional program returns the same result. In particular, it ensures that the programmer does not have to consider
in which order programs are evaluated, since eager evaluation will return the same result as lazy evaluation. However, it is still possible that an eager evaluation
may not terminate while the lazy evaluation of the same program halts. An advantage of this is that lazy evaluation can be implemented much more easily; as all
expressions will return the same result at any moment (regardless of program state),
their evaluation can be delayed as much as necessary.

## Parallel computing

*Purely functional programming simplifies parallel computing[5] since two purely functional parts of the evaluation never interact.*


## Data structures


*rely functional data structures are often represented in a different way than their imperative counterparts.[6] For example, array with constant-time access
and update is a basic component of most imperative languages and many imperative data-structures, such as hash table and binary heap, are based on arrays. Arrays
can be replaced by map or random access list, which admits purely functional implementation, but the access and update time is logarithmic. Therefore
, purely functional data structures can be used in languages which are non-functional, but they may not be the most efficient tool available, especially if 
persistency is not required.*

*n general, conversion of an imperative program to a purely functional one also requires ensuring that the formerly-mutable structures are now explicitly
returned from functions that update them, a program structure called store-passing style.*


