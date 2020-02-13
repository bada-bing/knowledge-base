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
