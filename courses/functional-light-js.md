[Functional-Light JS, v3 - Kyle Simpson](https://frontendmasters.com/courses/functional-javascript-v3/)
[Course Link](https://frontendmasters.com/courses/functional-javascript-v3/)
[Course Slides](http://static.frontendmasters.com/resources/2019-05-06-functional-light-v3/functional-light-v3.pdf)

Imperative Approach is primarily focused on how to do something;
- when reading such a written code you need to infer what it is doing (e.g., you need to figure out the purpose of a for loop)
  - the main problem is that the reader does something which he is not naturally gifted to do
    - he needs to execute the code in his head to understand it (he needs to imitate the process which is reserved for machines)
Declarative Approach is focused on what we want to achieve;
- and additionally it aims to answer the question "why"
  - sidenote: when explaining difference between declarative and imperative, Kyle mention importance of code comments
    - comments should not duplicate the narrative of the code
      - do not tell me that the code increments "i" for 1 value at a time, I can see that from the code. tell me why it is doing that
  - declarative style can highly help us to explain what and why are we doing that
- ❗❗ functional programming is usually more declarative than OOP which is usually more imperative
  - it is important to point out that this is higly relative (and not necessarily always applicable); there are no absolutes
    - e.g., forEach is more declarative to regular for loop but more imperative when you take map into consideration

Really Important: Dont forget DELIBERATE PRACTICE! In order to become familiar with FP, you will need to go through the phase where it feels not so nice and it is much more confusing and you struggle with it to understand it
- that is because it is new, and not yet familiar (and you are acustomed to some completely different approach to programming)

FP is actually more about math. All the code is provable to work if you write it in a good FP matter. (even though it is about math, you don't really need to know all the proofs to use it, basically same as with machine learning)
- FP is provable
- And really important! it is much more testable.
  - really good explanation by Kyle here
    - when working with the imperative code (and especially mocking of some dependency), we only partially understand the code (and how it works)
      - therefore, if we would understand it better, the tests wouldn't be such a big problem, but because of that semi-understanding we are just hoping it will pass
    - if you would understand the code well, it would pass from the start
  - ⭐ FP is compelling because it offers principles of programming which is based on real math
    - it will help you to focus your time on business time (instead of mixing it with how to achieve some stuff)
- Essentially all programming is about state management
  - most programs are essentially state-machines
    - at least most of the frontend-frameworks are
    - FP helps you to achieve that in a special manner


Closures are the essential part of FP!
- most features of FP depend on understanding closures
- recursion as well is highly useful
- observables help us to focus on asynchronous part of FP (data which we will have in the future)

What is a function (1.total, 2.deterministic, 3.no-side-effects)
  - function in a FP manner is not just a `function` keyword
  - function needs to return some output (needs to have a return keyword)
    - "functions" which do not have return value or do not comply with function FP definition are keywords
  - functions can not call "procedures", or otherwise they also become procedures
    - it needs to be the function in order to reap the benefits of FP (composition, chaining, mapping and all other)
  - about naming functions
    - function name should tell you about the semantic relationship between the input and computed output
- Pure functions - no side effects, return output based only on the input
  - inputs and outputs need to be direct (means input as parameters, and outputs returned using `return` keyword)
  - additionally, (at least in JS) function call is equally important as function def, in order to say that something is a function, we need to look at function calls (not only function def)
    - we use function calls (instead of procedure calls) in order to avoid side-effects
      - only if possible
    - side effects impure and water-down the benefits of FP and that is the reason why we aim to minimize them
      - and when we make side-effects (which are not avoidable we want to make them very obvious and be very intentional about them)
        - conclusion "avoid side-effects where possible, make them obvious otherwise"
  - the "pure" function can not be observed only in the function def... it needs to observe function call as well
    - additionally, the function can access some value from outside which is stored in some variable and still be considered pure
      - the point is that the varialbe is just a placeholder for a value, and if we can communicate that this value (in variable) does not change then we have a function
        - one way to communicate that is to use `const` keyword for that placeholder for a value
    - the biggest problem with side-effects is that when there are side-effects we need to mentally execute the whole program in order to understand a certain line or parts of the program
      - a solution how to avoid side-effects is to reduce the surface area of the code
        - [link](https://frontendmasters.com/courses/functional-javascript-v3/reducing-surface-area/)
        `function addAnother(z) => (x,y) => x+y+z`
        - the point here is that instead of having one function which sums x and y and access z from outer scope, we are passing this z as param, and therefore reduce the surface-area (and in that way side effects)
          - we don't need to look through the whole code to observe changes on z, it is only important at the point where z is called
            - now there is only one place where we can define z (and that is when it is passed as parameter)
          - this is also a form of partial application of value
            - we pass a value as input and remember that for later to be used together with other inputs

  really important point is to reduce surface area
    - the less places where some side-effects can occur, the easier becomes to reason and read and to rely on the code
  - pure function calls act in isolation (given the same input, they will ALWAYS return the same output)
    ```js
    function getID(obj) {
      return obj.id
    }

    getID({
      get id(){
        return Math.random();
      }
    })
    // this is what Kyle mentions about importance of function-calls considering if something is a function
    // considering this object, this function call is definetly not pure
    ```
  - Function purity is a level of confidence (it is not a binary characteristic (i.e., yes or no))
    - it is how confident is the reader that the function does what is expected
    - once again, function purity is about function calls (not function defs)
  - side-effects should be extracted (in order to make them obvious)
    - if we have a side-effect of writing some calculation result to db we extract writing to db and make it part of procedure
      - this way calculation is function which is not impured by writing to DB
  - the point is to structure the code in such a way that the core should be FP, and the side effects should belong to outer shell
Lambda expressions
First-class functions - accept other functions as arguments
	- e.g. Map()
	- e.g. Filter() - requires function which return bool as parameter
		○ Returns only members which got trues for the param function
Higher Order Functions
	- Functions which take other functions as parameters

https://medium.com/@BeardedTim/iteration-a-gentle-introduction-to-functional-programming-c59fcb0ab58d


Arugments define the shape of the function (especially the number of the arguments)
- parameter in the function definition, argument is the actual value passed in the function call

- Unary function - takes one input, and returns one output (this is the type of functions which can be used for chaining for example)
- Binary function - takes two inputs, and returns one output
- these two are by far most common used shapes of functions
  - other types of functions are n-ary functions

Here comes into play HOF (Higher-Order Function)
- function which returns as the output (or receives as an input) a function (or more functions)
- functions which do NOT receive (or produce) functions are called Single-Order Function


Important to understand with HOFs is that they serve as adapters
- they can take one function as input and adapt it (and return adapted function as the output)
- most of the features/functionality of libs like ramda and lodash are in the form of HOF

In other words, if we need to combine two functions of different shape, we can always create a HOF which will act as an adapter, and customize the inputs/outputs of one function so that it can work with other
  - this is called `Arguments Shape Adapter`
  - there are other types of adapters (of shape)
    - e.g., `Flip and Reverse Adapters`
    - Spread Adapter
      - there is spread operator for that "..." (but also the method called apply)

# Point Free
- defining a function without need to define its points (inputs)
  - in FP points refer to arguments
- essentially, it is about defining function using other functions

```js
getPerson(function onPerson(person){
  return renderPerson(person); // here we define a point which we are passing as argument (it is person)
})

getPerson(renderPerson) // this is a point free style (we are just passing a callback f-ction which we want to operate on "person")
// - this is called Equational Reasoning: if two f-ctions have the same shape, they are interchangable
// - e.g., in example above "onPerson" and "renderPerson" have the same shape and therefore are interchangable
// - therefore we can make the code simpler by defining the callback function without need to list the points
```

Be careful with DRY, in FP sometimes it pays off to be a little bit more repetitive if it will give more clear picture of the code

an example if we have isEven and isOdd we can define `isEven = v => (v % 2 ==1)` and `ìsOdd = v => !isOdd(v)`
- this is the example where we lose DRY in order to make more obvious the relationship between two functions
- there is more Point-free approach how to write functions which give negated results of other functions
  - look at complement https://ramdajs.com/docs/#complement

Point-Free style is more declarative style of coding
- when you define functions in terms of another function (like examples with isEven and isOdd) you gain the benefits of making the relationship between them much more clear

Closures are essential to FP
- importan distinction: variables which are part of the closure should not be re-assigned (or otherwise that would violate FP, same as with regular variables)
  - in general these variables which are stored as closures (i.e., which that inner function is closed over) should be immutable
    - otherwise, it creats many subtle bugs which are hard to detect and from the perspective of FP we lose function (i.e., function call) impurity


# Lazy vs Eager execution
- if the outer function creates the inner function which uses some closure from outer function
  - and if that inner function creates the result only when it is called, then that is LAZY execution
  - if the outer function would create the result for inner function, which would then only return it, that would be EAGER execution

points to consider for Lazy vs Eager
1. sometimes we want lazy if we are not sure that somebody is going to call the function at all
2. argument against it would be that we need to make that calculation every single time

- the technique to overcome this problem, and to gain best of both approaches is to use `memoization`
- `memoization` is included in all FP libraries, and what it does is that: you pass it a function, and for that function it monitors what inputs it receives, and if it already got that input, it has cached output... if not it will calculate the output for new input and then cache that (input, output) pair as well
- it does that for lazy functions
- memoization is not so useful for functions which are easy to compute and get all different kind of inputs
  - it shines for cases where the calculation is heavy (and preferably, often with the same input)

Kyle makes a good exmaple on memoization
- you can make your custom memoization and put it in your code, but you risk to lose readability (and your code becomes more imperative that way)
- it is better to leave that task for the functions which are designed for that (and are proven to work)
  - it is not the question if "side-effects" or "effects" which increase risk of impurity happen, it is also the question where they happen


### referential transparency
- the function call can be replaced with its return value and it will not affect the rest of the program
  - this means that if `a(3)` returns "aaa" I could inside of some expression use either `a(3)` or `aaa` and it would not be a difference to any part of the program


Generalized vs Specialized F-ctions
- we tend to have this idea that we should only put code into a function if it starts repeating itself,
- but it should not only be that, it should also be that the piece of code get its semantic description
- and function call describes its purpose

when we are aiming to write a relation between more general and more specalized functions (like in example with currying) we should write most general parameters as the most left params (first params) and the most specalized params (last params) as the most right params
  - i.e., data is most specific input (should go on far right) and callback/functionality should go most right (since it is most general input)

# Partial Application and Currying (Used for Specialization of F-ctions)
- specialization adapts shape
- partial(fn, args)  - it creates partial application function from function "fn" by presetting defined arguments (args)
- currying - more common than partial applciation
  - the name comes from the name of the person who invented the method

# Composition
- ⭐ Composition is declarative data-flow!
  - i.e., flow of data through a series of operations (which are defined declaratively (instead of imperatively))
  - and dataflow is the most important part of all programs! programs are built around dataflows
  - programs are about state transitions which are determined by dataflows
  - because dataflows are so essential, then we should declare our dataflows in clear declarative manner (rather then having it implicitly (and imperatively) linked)

Functions should express semantical relation between input and output
- in general they should help us abstract (and reason about our code)
- e.g., if we have some price and we want to calculate shipping rate we would have one function for how to calculate it and the other for to append it to the current price

Composition works in right-to-left order
- we first execute the last passed function, and then go in direction to the first passed function
- composition (in general) works with unary functions

Compose: Riht-To-Left
Pipe: Left-To-Riht

# Immutability
- it is about things not being changed unexpectedly
- i.e., change of state should be intentional (not accidental)
  - immutability is more about how do we control mutation/change of state

2 Types of Immutability:
1. Assignment Im. - when you assign something to a val or prop it is not allowed to be reassigned
   - e.g., if you have `const` you cannot reassign its value
     - also you can't declare `const` without assigning it the value
   - intersting point: FP in general tries to avoid assigning variables (the data should be passed to and from functions)
   - the problem with const comes to when we are mutating properties of object or elements of an array
     - the const is not re-assigned but the object is being mutated
     - we interpret "const" as `the value is not going to change`, but it is rather `the assignment is not going to change`
       - const is more like a "final" (like the final assignment of the variable)
2. Value Immutability
   - assingments are lexically scoped (which makes them not portable outside of their scope)
   - and values which are passed by reference are completely portable (which makes the problem of their mutability a big risk)
     - and this is the biggest problem and cause of the most of the bugs: value being mutated in the way we didn't expect
   - In order to mitigate this problem, we want mutable data-structure to make a read-only
     - we do that using `Object.freze(obj)` (read-only data-structures are structures that never need to be mutated)
     - this is also important to communicate to the reader of the code (this object is not going to be mutated inside of this method)
     - important point, never change the object you are passing in as input (instead copy it, update the copied version and return that updated copy)
       - since you can't count that the passed object will be passed with Object.freeze when writing functions you always need to assume that it is going to be passed read-only object, and therefore in function you should always create a copy of the object
   - Immutable Data Structures (Immutable.js)
     - they provide structured mutations on data-structures (important for pure FP)
       - e.g., with such structures if the list is mutated, it does not mutate directly the list but returns the copy which is mutated
     - check that library and how it is used: https://immutable-js.github.io/immutable-js/
- Important: when you declare `const arr = [...]` (think if you want to use Object.freeze or const, because const does not solve the problem of being able to mutate the array)

# Recursion
- usually when working with recursion, the way of thinking should be in direction "I want to reduce my problem set"
  - e.g., If we have a string, with recursion we should aim that each following call (in recursion) deals with a subset of the string "which was passed to the previous call"
    - e.g. "hello" -> "hell" -> ... -> "h"
- the other types of problems is called "divide and conquer" - it is about "can I eliminate half of the problem"


- how to make recursive function
  - 1. base condition (how to know when to stop) (e.g., an empty string)

Recursion is designed to be a declarative approach (not an imperative approach, like a loop)

the biggest problem with recursion - stack overflow
- each time a function is executed its context is stored in the stack frame

# PTC (Proper Tail Calls)
- TC39 Proposal to implement Tail Calls in JS
  - this is a technique used in recursion to prevent out-of-range (stack-overflow) errors by reusing the same stack frame for each instances within recursion
  - instead of creating new frame for each function call, one frame would be reused
    - it needs to have a form of `return otherFn(x, 1)` (that will ensure that the current stack-frame can be reused for `otherFn`)
    - e.g., `return first + countVowels(str.slice(1))` - this can not be a proper tail call since after countVowels finishes it needs to add that value to `first` and therefore current stack-frame can not be used for the following function

## another option is CPS (Continuation Passing Style)
- i.e., this is essentially a callback
- v => v (this is known as identity function, function which return the argument which is passed to it)

## Trampoline
- CPS is almost never used, but trampoline is implemented in the FP libraries and used often
  - research on that
  - https://github.com/DefinitelyTyped/DefinitelyTyped/issues/34528


# Lists (actually, Data-Structures)
- even though it is most of the time related to arrays, these type of FP techniques should be doable on any type of data-structures
- applying the operations which we learned which work on single values (single inputs) to work on collection of values

- Important Concept: Functor
  - Functor is a value (or a collection of values) over which the values in it can be mapped
  - e.g., since we can call a .map on array, that array is a functor
- each value which implement .map is considered as a functor
  - it is a value I can map an operation accross
- map is a transformation operation
  - functor has to be a pure function
    - can mutate stuff, it needs to return new objects
    - it results in the same data-structure as it received as input
      - if it received array with 3 els, it will return the array with 3 el
- potentially, map could be used for any kind of els (map string into another string, map a number into another number)
  - the important point is that we are applying the same transformation across the whole data-structure

1. Map: Transformation
2. Filter: Inclusion
   - the point with filter is that we are not doing something which is semantically clear from the english language
     - in general when we would filter something, we would "filter out"
     - but in programming it means "filter in", which things are satisfying the condition
3. Reduce: Combination
   - it is a very general operation
     - in most cases it uses elements of data-structure and combines them
     - but this combination can be anything
       - it can be addition, multiplication, but it can be as well "creating an object" which hold these els as properties, it can even reduce it to a list which is even bigger than the original list
   - reduce is so general, that both map and filter could be implemented using reduce
   - there is also reduceRight which goes from right to left
     - and if you would pass it an array of functions, you could create a composition function out of it
     - if you would pass an array of function to regular reduce, you would get a "pipe"
       - essentially in both cases the "reduction part" is the invocation... passing the accumulator part to the current el (fn) (or something like that)


- as a good programming habit, aim to use `.concat` (instead of `.push`)
  - concat contactenates the value to the array but it does that in a new array, you get the new array as a result

Functions which have the same shape (e.g., unary fns) by equational reasoning can be interchanged, and therefore mapped together
  - they all produce the same shape of the output and require same shape of the input
  - in such cases, we don't need to pipe maps one after each other, we can use the composition for their map function
    - that is called **fusion**
  ```js
  function add1(v) { return v + 1}
  function mul2(v) { return v * 2}
  function div3(v) { return v / 3}

  var list = [2,5,1,3];

  list
    .map(add1)
    .map(mul2)
    .map(div3)

  // - this is the fusion
  list.map(compose(div3, mul2, add1))
  ```


# Transduction
- an advanced technique
- used to combine multiple maps, reducers, filters
- 🌟 transducer is a composition of reducers
    - we want to transform mappers and predicates (for filters) into reducers and then we want a mathematical transform which allows reducers to be composed together
    - transducer uses the same compose as the regular functions of the same shape
      - but then if we want to use filter or map we would use `filterReduce` and `mapReduce` (these are special kinds of reducers)
    - and then we are going to combine everything inside of `transduce`
      - here is [ramda docs on transduce](https://ramdajs.com/docs/#transduce)
- there is alternative to transduce and it is called [into](https://ramdajs.com/docs/#into)
  - into does not use combinator (fn which is passed to reduce) since it tries to guess it base on the datatype of the collection
    - e.g., it will add numbers if the collection contains numbers
    - if you would like to use different combinator (e.g., multiplication) you will need general type of transduce
  - transducer is a high-order reducer

# Monad
- FP Data Structure (they are functional friendly data-structures)
- it is a data structure which holds one discreete value
  - a wrapper around the value with a set of behaviors, that is going to make these value much easier to interoperate with other values in a very specific kind of a way
- Monad turns the single value which it wrapps into a functor
  - a monad if it implements a map then it is a functor
- Def (from Kyle) - A pattern for pairing data with a set of predictable behaviors that let it interact with other data+behavior pairings (monads)
  Types of Monads:
    - Just - this is a wrapper around a single value
      - has 3 methods: map, chain (known as `flatMap` and `bind`), ap
    - Maybe (I think this is like either monad from the other course)
      - [diff between either and maybe monads](https://stackoverflow.com/a/42558527)


# FP in Async

Synchronous, Eager FP (work with regular arrays)

```js
var a = [1,2,3];
var b = a.map(v => v*2)
b //[2,4,6]
```

Async - Lazy, Over-time FP

- Observable is data structure for async programming
  - it is like a spreadsheet (if you have one column, you can define other columns in terms of that column, and whenever you add values to the first column you will get mapped values in the other column)
  - there is a relationship between these two columns, in the form of mapping
