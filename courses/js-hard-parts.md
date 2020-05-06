The outer function is "Higher Order Function"
	- Higher Order function is any function which takes in or returns out a function
	- and the function we insert in is called "callback function"
	- this helps to write more declarative and more readable code for sure

You should seek for the balance between clarity (readability) and legibility
	- legibility is defining function in the shortest notation possible
		○ e.g., x => x*2
		○ instead of "function (x) { return x*2}
			§ this is known as "classical function declaration style"
	- clarity is when you make it easily understandable
		○ when you are clear in your intentions
	- you should aim for a balance between these two

Regarding the execution context
	- when the function invocation reaches the final line… everything from the execution context is deleted except the return value (which is passed to outer context)
	- Functions have associated with them the execution context in which they are defined
		○ they have magic property [[scope ]]
		○ this enables the closures to work like they work
			§ that functions can reach for variables which are out of their context (but from the outer context which is not destroyed but persisted because of this [[scope..] magical property
		○ These function are defined as result of invoking their higher order function (in this case these higher order functions are returning these "smaller" functions which have this [[scope ] ] property
		○ Essentially this enables these "smaller" functions to remember / to be aware of previous runnings of that function


The locale memory where the state of the variables (accesed through the execution of that function) is persisted is also sometimes called (Locale) Variables Environment


What is Scope?
	- Scope is the set of rules which define for each line (which is executed) which data does it have available
	- JS has Lexical (or Static) Scoping
		○ Where I save my function determines for the rest of that execution (of that function) what data it will have access to
			§ Lexical means physical positioning on the page!
				□ I phyiscally position some smaller function inside the running of outer
				□ Lexical Sope enables closures
		○ It is not Where I run it … that would be dynamic scoping

[UNSORTED CONTENT - BEGIN]
In JS call stack is called Task Queue and apart from main Task Queue there are Callback Queue (eg from setTimeout) and called Microtask Queue (from promise.then)
- microtask queue has priority over callback queue
- check "starving callback queue"
- all functions passed to then of promise go into microtask queue
- functions passed to Web Api from browser go into callback queue

Time in setTimer essentially describes when the callback function will be added to callback queue .. not when it will be executed

Essentially promise with then stores the callback which will be executed and only once it resolves(or rejects) it will put that callback in the microtask queue
- what triggers onFulfillment is the change of promise state.. eg from pending to resolved
[UNSORTED CONTENT - END]

[JS Hard Parts - v2](https://frontendmasters.com/courses/javascript-hard-parts-v2/)
[Lecture Slides](https://static.frontendmasters.com/resources/2019-09-18-javascript-hard-parts-v2/javascript-hard-parts-v2.pdf)

- [Principles](#principles)
  - [Pillars of JS - How JS Engine works](#pillars-of-js---how-js-engine-works)
- [Execution Context](#execution-context)
    - [Lexical Scoping](#lexical-scoping)
- [Call Stack](#call-stack)
- [Callbacks](#callbacks)
- [Closure](#closure)
- [Async JS](#async-js)
  - [ES6 Promises](#es6-promises)
- [Classes & Prototypes](#classes--prototypes)
- [JS Classes](#js-classes)

# Principles
## Pillars of JS - How JS Engine works
- JS Engine both compiles and interprets the code - uses JIT Compiler (Just-In-Time)
  - How it works:
    - it reads the code and as soon as it encounters the first line it puts a couple of references in Global Memory (Heap)
    - later it tries to optimize code
  - Google's V8 Engine (JS Engine used inside Chrome and Node.js; SpiderMonkey in Firefox)
    - Consists of 2 main components [How JS Works Pt.1 - An overview of JS Engine](https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf)
      - Heap Management & Call Stack
        - JS Engine runs in hosting environment
          - it includes Web API, Event Loop and Callback Queue

- 3 Main Components: Call-Stack, Global Memory (& Thread of Execution) and Execution Context
- Concurency & Event-Loop
  - asynchronous-callbacks


**Thread of Execution**
- When JS runs it goes through the code line-by-line and executes each line
**Memory**
- the Data and Code (Functions) are saved in Memory to be used later
  - Local Memory of certain function is called **Variable Environment**

# Execution Context
- http://davidshariff.com/blog/what-is-the-execution-context-in-javascript/
- When we run a certain function, this is the context of running a function (i.e., Execution Context) contains 2 important parts:
  - 1. Thread of Execution
  - 2. Memory
  - Both of them are local (since they only apply to the local context of running a function)
- Context is essentialy the scope

  - There is only 1 global scope / variable is in global scope (Global Execution Context) if it is defined outside of a function
  - When a function is called the JS engine also uses Global Execution Context and the Call-Stack
    - Each function when invoked creates a new scope
		- the engine puts the function into the Call-stack
		- At the same time engine allocates a Global Execution Context
			- this is the **global environment** where our JS code runs
			- The function is put into the Global Execution Context, but all of it internals (e.g., inner variables) are put into Local Execution Context
	- Each function creates its own execution context
  	- The browser always executes the execution context [SCOPE] that is at the top of the execution stack

### Lexical Scoping
- Lexical Scoping defines how variable names are resolved in nested functions:
  - inner functions contain the scope of parent functions even if the parent function has returned (closure).
  - i.e., functions have access to variables from the calling scope
    - https://medium.com/dailyjs/i-never-understood-javascript-closures-9663703368e8
- Whenever you declare a new function and assign it to a variable, you store the function definition, as well as a closure. The closure contains all the variables that are in scope at the time of creation of the function.
- Apart from the function scope there is also a block scope (for block statements)
  - it is defined with { ... } and it requires let and const
	- does not work with var

- Scope - the accessibility of the function
- (Calling) Context - the value of `this` in some particular part of the code, i.e., `this` refers to the context of the function/running code ( which object is associated to the function as its context)
  - In the case of constructor function it is a brand new object
  - in Global scope context is always Window (Browser) or Global (Node.js) object
  - If scope is in the method of an object, context will be the method the object is part of
    - but if is in the function (which does not DIRECTLY belong to the object(e.g., inner function defined inside of some method)) it will belong to the Global object
  - arrow functions use the this variable from its outer lexical environment. (the function/location it was defined in) This is useful for nested functions, but they’re no good as methods
	- Use arrow functions for callbacks and nested functions.
	- Don’t Use arrow functions for methods and constructors.

- What is scope?
  - ⭐[article about scope](https://scotch.io/tutorials/understanding-scope-in-javascript)
- Scope - determines visibility/accessibility of variables, func and objects in some particular part of the code during the runtime
	- reason for having scope is security (only having what you really need at disposal)
	- 2 Types of scope
		- Global - lives as long as your application lives
    - Local - lives as long as your functions are called and executed
  - Important point is that Lexical scoping is the reason why you are not supposed to use arrow functions as methods of object
    - more info here - [SO link](https://stackoverflow.com/questions/31095710/methods-in-es6-objects-using-arrow-functions)
      - it is fine to use them in inside functions of methods (because of lexical scoping it will share `this` with the method in which it is defined)

	- If you want to disconnect this in a class from the calling context use an arrow function

# Call Stack
- JS keeps track of what function it is currently running (i.e., in which function is the thread of execution)
- When F-ction is run, it is added to the call stack
  - When it returns, it is popped out from Call Stack
- LIFO principle
  - Whatever is at the top of stack is currently running
- JS is single threaded and has single Call-Stack
  - Call-Stack is a data structure which records where in the program we are
  - Each entry in the call stack is called Stack-Frame
  - That is how stack-traces are constructed when exceptions are thrown
    - the state of Call-Stack when exception happened
  - Blowing the stack - reaching the maximum call stack size


# Callbacks
- Functions are first-class citizens in JS (means that they are objects, like all other objects)
  - assigned to variables and properties of other objects
  - passed as arguments and returned from functions
- This enables core aspects of functional programming - map, filter, reduce
- This makes code more declarative/readable

**Higher-Order** Function - takes in a function as a parameter or returns a function
  - Higher-Order Functions enable Declarative readable Code (i.e., map, reduce, filter)
**Callback** - function which is passed to (or from) higher-order function
- Callbacks are a core aspect of asnc JS (they are under-the-hood of promises and async/await)

legibility vs readability
- arrow functions allows for better legibility of the code (it takes less space, and probably you can find more stuff at one place)
- but they compromise readability since it is now harder to read the code and takes more time to reason about it

# Closure
- In short, Closure is related to returning an inner function from the outer function, where the behavior of inner function directly depends on some variables from the scope of invoked outer function (which means that this state/scope of the outer function invocation is saved, so that it can be used whenever the inner function is called)
⭐- When function is defined it gets a bond to the surronding Local Memory (Variable Env) in which it has beed defined
    - in the case of closure this is the context of the execution of outer function
    - essentially we are maintaining a bond to outer's live local memory (which is attached to the definition of the inner function)

- Many design patterns in JS are based on the concept of closures
  - important one: Module pattern, Iterators and Generators, Callbacks and Promises rely on closure to persist state in async environment
❔ - Build iterators, handle partial application and maintain state in an async world
  - Essentially, closures provide the state saved from the memory when we were executing some function
    - so it is state which comes from the Function Execution/Invocation and it is stored in the memory as long as potentially it is required for a certain function which was created during that Function Invocation
  - Closures are starting with functions which are returning a function
    - the context/scope of the function invocation which returned some function is the callback

  - When a function is defined, it gets a bound to the surrounding Local Memory ("Variable Environment") in which it has been defined
    - the closure is essentially maintaining this bond (outer local memory is attached to the newly defined function, even though that context of executing outer function is gone)
      - when we execute the inner function to search for a variable, the JS Engine first looks in the local context, then in the closure in which the function is defined

  - JS provides magical property [[scope]] of returned inner functions (which are directly tied to Local Memory (Variables Env) of the execution context of outer memory which returned generated inner function)
  ```javascript
  function createInsideFunction(multiplier) {
    const multiplier_new = multiplier*3;
    function insideFunction(num){
      return num*multiplier_new
    }
    return insideFunction
  }
  const generatedFunction = createInsideFunction(5);
  const res = generatedFunction(3);
  ```
  The concept of closure can be observed in such a way, that returned function "insideFunction" depends on the invocation of outer function (more specifically on the variable of outer function "multiplier_new")
  - As long as the inner function is stored in some variable this closure (the memory/state of the outer function invocation will be saved)

# Async JS
- Promises, Async/Await and Event Loop
- Together with Event Loop are important Microtask Queue, Callback Queue and Web Browser features (APIs)

Why is Asynchronicity important in JS
- JS is single threaded
- 1 Process, 1 Thread, 1 Event Loop
- JS Engine executes code **Synchronously** (in 1 thread)

Since there is only one thread browsers need a way how to handle some intensive tasks so that they do not block the UI
- that means that some code executed in JS is handed over to other browser's threads
- an example is setTimeout...
How it works is that we provide the code which will be executed upon completion (callback) and JS engine goes further in execution (does not block on the line and wait for the results)


## ES6 Promises
  - that get returned immediately when we make a call to a web browser API/feature
  - (e.g. fetch) that’s set up to return promises (not all are)
    - Return a placeholder for the data we expect to get back from the web browser feature’s background work
    - then method will automatically trigger the attached function to run (with its input being the returned data)
      - Added using .then method to the hidden property ‘onFulfilment’

  ```
  function display(data){
    console.log(data);
  }

  const futureData = fetch("twitter.com/miki/tweets/1")
  futureData.then(display) //once you have the data, display them
  console.log("but first console log this");
  ```


  - Rules for the execution of Async delayed code
    - Promise-deferred Functions are part of a micro-task queue
    - callback functions are part of the task queue (called when Web Browser Feature API finishes its stuff)
    - Add the function to the CallStack (i.e., run the function) when:
      1. Call-Stack is empty & all global code run (Event Loop continiously check this condition)
    - Functions in microtask queue have higher priority than functions in Callback queue


# Classes & Prototypes
- Prototype Chain
- difference between __proto __ and prototype

Different ways to create an object
`const user = {};`
`const user = Object.create(null)`

```
function userCreator(name, score){
  const user = {
    name,
    score,
    incrementScore = function(){
      user.score++;
    }
  }
  return user
}
```
- The issue is that every time we create new object using this function all instances create the same function `incrementScore` (instead of just sharing this function code)

- `Object.create()` specifies the prototype we want to use when we creating the object, this way we can store all functions/methods in the prototype (and have one implementation which is shared for all instances)

```
function userCreator(name, score){
  const user = Object.create(userFunctionStore);
  user.name = name;
  user.store = store;
  return user;
}

const userFunctionStore = {
  increment: function(){this.score++;}
  decrement: function(){this.score--;}
}
const user1 = userCreator("miki", 0);
user1.hasOwnProperty('score');
```

- We use prototype chaining... user1 has the prototype userFunctionStore... but this function also has its own prototype (Object.prototype)
  - all objects have default __proto __ property default set to `Object.prototype`
    - prototype of an object is accessed through its hidden property __proto __


- In a method `this` refers to the owner of the method
- In a function `this` refers to the Global context (refers to Global Object [object Window])
  - that is the default binding for this
  - in strict mode it is 'undefined'

https://codeburst.io/the-simple-guide-to-this-in-javascript-24a6638b1105


"new" keyword - simplifies the process of creating constructor functions

# JS Classes
JS does not really have classes; The **class** is syntactic sugar for 'prototypical inheritcance'
- essentially you are writing methods of the object in the prototype (specified in constructor function)
  - JS uses Prototypes, singleton objects which other objects inherit from
- class enables you to write everything in one place
  - A Class is blueprint for create object instances (a prototype IS an instance)
