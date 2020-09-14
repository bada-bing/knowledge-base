# Features introduced in ES6 (ES2015)
* Object Destructuring `const { var1, var2 } = existing_object_1`
 - Destructuring is about *assignment* not about declarations
 - Designed to make easier extraction & assignment of values to variables by defining more **declarative** approach
* TIP1: Don't be afraid to use empty space when destructuring… make it more readable
```javascript
{
  var1,
  var2
} = obj1
```
is often better than:
```javascript
 {  var1,  var2} = obj1
```

# Modules ES6
[SO Link - When to use Curly Braces for ES6 Imports](https://stackoverflow.com/questions/36795819/when-should-i-use-curly-braces-for-es6-import/36796281#36796281)

# Console
[console.dir](https://developer.mozilla.org/en-US/docs/Web/API/Console/dir)
Check the following Console methods
- console.time()
- console.timeEnd()
- console.timeLog()
--------------------
- e.g.,
- console.time("execute")
- console.timeEnd("execute")

# MISC
Difference function expression vs function statement vs function declaration
	- https://medium.com/@mandeep1012/function-declarations-vs-function-expressions-b43646042052
- I think that Function declaration is: `function myFunc()`
- and Function expression is: `const myFunc = function()`
