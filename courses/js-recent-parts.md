[JS: The Recent Parts - Kyle Simpson, @getify](https://frontendmasters.com/courses/js-recent-parts/)
    - Slides & Code Exercises need to be downloaded
    - For Loop (i.e, for…in vs for…of)
      - for..in iterate over keys of the itterable
      - for…of iterate over values of the iterable
		    - Object is not an itterable!
		    - https://alligator.io/js/iterables/
		    - https://scotch.io/@devGson/understanding-iterators-and-iterables-in-javascript

ES3 was introduced in 1999, ES5 in 2009 (full decade of nothing happening), but ES6 was also introduced only 6 years later in 2015
- from now on they also changed the name of the language, it was not ES7 but ES2016
- there are 5 stages (from 0 to 4) of TC39 proposals (until final stages nobody knows when the feature is going to be implemented)
- ES6 is important for the evolution of JS, because it provides an important narrative of moving JS to being more declarative language

for browser support Transpilers are really important (i.e., Babel), they take features from some standar (i.e, ES2016) and create equivalent which is compatible in some older form (i.e., for IE 9)


Features

# Strings
## Template Strings ``
- in other words, this is a "string interpolation"
Tagged Templates - https://wesbos.com/tagged-template-literals/
- e.g.,
```javascript
  var msg = formatCurrency`The total Amount for your order is ${amount}`;

  function formatCurrency(strings, ...values){
    ...
  }
```
- important: tagged filter functions - most of the time you don't need to write them yourself, just search npm packages and in internet and there are many tag functions for tagged elements
- tagged functions do not even need to return a string, there are use-cases where they return regex (because regex needs to be in one line in js, it is quite hard to read and write... and therefore tagged functions can be used to mitigate that problem- tagged function will return as a result a regex)
  - in a similar way, there are tagged functions for jsx (react syntax for rendering elements)


## String Padding & Trimming
- JS now officially supports both padding and trimming of strings
  ```javascript
  var str = "Hello";
  str.padStart(5); // "Hello" doesn't add any padding, because it is already 5 characters long string
  str.padStart(8); // "   Hello"
  str.padStart(8, "*"); // "***Hello"
  str.padStart(8, "12345"); // 123Hello"
  str.padStart(8, "ab"); // abaHello"
  str.padEnd(8); // "Hello   "
  ```

  ```javascript
  var str = "  Hello \t\t";
  str.trim(); // "some stuff"
  str.trimStart(); // "some stuff     "
  str.padEnd(8); // "  some stuff"
  ```

# Object Destructuring
- *decomposing a structure into its individual parts*
- object destructuring is about extracting values and assigning them in a more declarative manner
  - it is not about declaration of variables (you don't need to use let/const/var in this kind of expressions, it is just for convenience and variable could already exist before the expression)
- the pattern does not need to take into account part of the structure which are not relevant for you, you can only extract properties/elements which you care for
- e.g.,
```javascript
let [
  {
    name: firstName,
    email: firstEmail = nobody@none.tld
  },
  {
    name: secondName,
    email: secondEmail = nobody@none.tld
  },
  ...otherObjects
] = getSomeRecords();
```
on the left-hand we have the syntax/pattern which is describing the structure/(what kind of value) which we expect on the right side of the expression
- in this case, there is a property "name" in this object and we are assigning it to a variable called "firstName"
- email has a default expression "...= nobody@none.tld" (if there is no email in this object, then use the default value)
- otherObjects is an array of all other objects from this array (... is called rest syntax)
  - if there are no other objects it will return empty array
  - rest syntax needs to be at the end of the pattern
also, you can define default values when destructuring and creating new objects or defining function signatures
	- it is easy to forget them, so one suggestion is to define a linting rule to remind you that you should add them
	- ⭐ eslint has such a rule


if you need the reference to individual parts but to the full object as well you can do that as well
```js
let [
  el1,
  el2,
  ...rest
], fullObject = getData() || [];
```
- in the case that getData() returns falsy value we have a fallback of an empty array

destructuring can be used for swapping values as well
```js
let x = 10;
let y = 20;
[y, x] = [x, y] // y = 10 & x =20
```
- this can be interpreted as "I want y to take the first position of the structure on the right-handside and x to take the second position of the same structure


we can do destructuring direclty in parameter positions when working with functions
```javascript
function data([el1, el2 = "some_value"] = []){
  //do something with el1 and el2
}
```
- this "= []" ensures that even if the passed argument is falsy value we will use defualt value (empty array) and return gracefully instead of throwing a type error

```javascript
function data () {
  return {
    a: 5,
    b: {
       c: 3,
       d: 4
       }
    }
}

var {
  a,
  b, // this is not the error... two times is b referenced (first one to hold reference for the whole object and in second one we destructure b to get its subparts - c and d (or var1))
  b : {
    c,
    d: var1 = 42 // in this case we will have variable with name "var1" and it will either be value of d or 42
  } = {}
} = data() || {}
```

- js does not have named arguments ... it only has positional arguments
```javascript
function getData(store = "person-records", id = 0) {

}
```
- in this case position of arguments matter... the first argument is always going to refer to store
- instead we can use object destructuring to mimic named arguments
```javascript
function getData({ store = "person-records", id = 0 }) {

}
```
- pro tip (if the function has 3 or more inputs, consider always using this object destructuring as a pattern (instead of simple positional parameters))
  - downside to this is that you need to know the name of the property which will be used as parameter
  - think about this again (VS Code shows you the code signature for positional arguments, and I am not sure if you get that if you put everything inside of an object)
# Array find() / includes()
- [find](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find) works like filter() ... it will return you the FIRST element of array which satisfies the criterion which you specified in "filter" function
```javascript
const array1 = [5, 12, 8, 130, 44];

const found = array1.find(element => element > 10); // returns 12
```
findIndex will return you the index of the first element which satisfies criterion
- if find does not find an element which satisfies criterion it will return "undefined"
  - this can be problematic if you are searching for "undefined" objects, and you can't know if it found undefined or didn't find a match
  - luckily, from ES2016 there is "includes" which returns true or false if the value exist in array
  - find returns value, findIndex returns index and includes return boolean value
# Array flat() / flatMap()
- these are methods which Jafar was developing in observables course, i.e., `concatAll` and `concatMap`
- you can provide as parameter desired level of flattening e.g., `someArray.flat(1)` it will only flatten one level deep
  - it means that direct elements of the array will be flattend, but if their elements are still arrays, they will not be flattened
  - `flatMap` is same like doing map and then flat, but more efficient, since it does not need to create this intermediate array to store mapped data which will be flatten
    - flatMap also only works with one level of flattening (like flat(1)) and you can't change that


# Iterators, Generators
Iterator - Behavioral Design Pattern for OOP languages
- standardized way of iterating through data sources
- the way to consume values from some data source one at a time
- you construct a controller which provides you the view on that datasource by giving you one value at a time
  - you do that by calling `.next()` on iterator over and over again
ES6 defines Iterable Protocol
  - strings and arrays are iterable (they implement that protocol)
  - `iterable` is something that can be iterated
  - you create iterator to consume values of the iterator

```javascript
var hi = ['h','i',]
var it = hi[Symbol.iterator]();
it.next(); // {value: "h", done: false}
it.next();
it.next(); // {value: undefined, done: true}
```
- `for .. of` loop takes iterables and iterates over them and give you the iterated values
- `...` spread operator also consumes an iterator
```javascript
var str = "Hello"
var letters = [...str]
letters;
// ["H", "e", "l", "l", "o"]
```

Array and Strings have iterators, but default Object does not!
therefore, you will need to create it yourself, and this is how
```js
var obj = {
  a,
  b,
  c
  //this is a factory function since whenever you call [Symbol.iterator]() it will give you a new iterator
  // - it is important that the iterator has next method
  [Symobl.iterator]: function() {
    var keys = Object.keys(this);
    var index = 0;

    return {
      next: () => {
        (index < keys.length) ?
        { done: false, value: this[keys[index++]]} :
        { done: true, value: undefined } :
      }
    }
  }
}

[...obj] //this would extract property values and put them into an array
```
- the shown approach is an imperative way how to create Iterators, on the other hand:
- Generators give us a declarative way of creating Iterators
  - added in ES6 (2015)
  - have * in front of the name
    - `function *main()`
  - generators when run they produce an iterator
    - essentially iterator is attached to generator
    - it uses yield keyword for the iterator to contain values to be iterated over
      - important thing, you should not return values from generator (you should yield them)
      - return keyword should be reserved for the final result provided by iterator `{value: undefined, done: true}`
- iterators produced by generators do not hold the whole result in memory (they yield one result at a time, and that is why we use "yield" as a keyword)
  - generators are functions that can be paused and resumed
  - generator uses yield to "yield" value and pause its execution (similar like return returns value and then exits out of the function)
    - therefore, generators do not load into the memory all of its items all at once (like you would if you have list)
- Iterator contains a set of values in a sequence. We can go through the elements in an iterator with a for loop.
- by default iterator of an iterable is retrieved using `iterable[Symbol.Iterator]()` iterator is also an iterable
  - this means that you can provide it in for of loop or in ... spread syntax

- Yield is like rerturn statement and the difference is that it suspends the execution context.. it doesnt destroy it like return

# RegExp Improvements
- lookaround (lookBehind() together with lookAhead)
  - Sometimes we need to find only those matches for a pattern that are followed or preceeded by another pattern.
  - [article](https://javascript.info/regexp-lookahead-lookbehind)


```js
var msg = "Hello, world";

msg.match(/(l.)/g); // [ll, ld] (why does not return "lo")
msg.match(/(l.)$/g); // [ld] - The $ is symbol for the end of a line (so match "l." only if it precedes directly $)
msg.match(/(l.)(?=o)/g); // [ll] - look ahead: only give me pattern matches which come directly before "o"
msg.match(/(l.)(?!o)/g); // [lo, ld] - negative look ahead: only give me pattern matches which DOES NOT come directly before "o"

msg.match(/(?<=e)(l.)/g) // [le] - look behind
msg.match(/(?<!e)(l.)/g) // [lo, lg] - negative look behind
```


## Named Capture Groups
- for capture groups we use parentheses "()" -
- () are not used just for grouping but also for capturing
- capture group is essentially a way to match a sub-pattern and pull it out in a separate way
  - also we can use capture groups for back references inside of regex pattern

```js
var msg = "Hello World";
msg.match(/.(l.)/); // [ell, ll] //"ll" is the result of the capture group (it is a subpattern of a bigger pattern)

msg.match(/([jkl])o Wor\1/); //[lo Worl, "l"] the "l" is actually matched using capture group (\1 - ref to capture group)
msg.match(/(?<cap>l.)/).groups; //{cap: "ll" - this is how to use named capture groups
msg.match(/(?<cap>[jkl]o Wor\k<cap>)/); // ["lo Worl", "l"] this is how to use capture group as a back reference in regex
msg.replace(/(?<cap>l.)/g, "-$<cap>-"); // "He-ll-o Wor-ld-" (pay attention, here is a global flag, so each instance of "l." will be replaced; two lines above you didn't have /g flag, so it captures only first instance "ll")
```

\g - global
\i - case-insensitive
\m - multiline
\s - dotall mode
  - "." character matches all character EXCEPT new line chars
  - dotall changes that, and includes even "\n"
\u - unicode aware mode
  - regexes work typically with ASCII char set (but this works with unicode as well)

```js
// you can use template strings to write string in multiple lines
var msg = `
The quick brown fox
jumps over
the lazy dog`;

msg.match(/brown.*over/) //null
msg.match(/brown.*over/s) // ["brown fox\njumps over"]
```
- in order to prevent regex algorithm from being greedy when providng ".*" you can prevent that with question mark (and then what follows is the rest of the pattern )
  - better explained here https://frontendmasters.com/courses/js-recent-parts/regex-solution/
    - around 2:30
    - also check this: https://stackoverflow.com/questions/11898998/how-can-i-write-a-regex-which-matches-non-greedy
    - https://www.itworld.com/article/2786107/regular-expression-tutorial-part-5--greedy-and-non-greedy-quantification.html

# async ... await



# async* ... yield await

essentially, `await` is the keyword which we use in the async-sync pattern (to use async code in a synchronous manner) in order to pull
- we pull the data from a promise once it is resolved

on the other hand generators with their `yield` keyword are based around pushing data
- they are yielding or pushing data to consumers


from ES2018 you can use a special function which is both async and a generator function and uses this syntax `async*`

a really good example is...
if we have an array of network requests, like 1000 of them, in the classical async function we would wait for all network requests to be resolved before we would return the results
- with async* function we could yield results immmediately as we get them (and not have to wait for all network req to be resolved first)

```js
async function *fetchURLs(urls) {
  for (let url of urls) {
    let resp = await fetch( url );
    if (resp.status === 200) {
      let text = await resp.text();
      yield text.toUpperCase();
    } else {
      yield undefined;
    }
  }
}
```
- this type of functions has its own type of for of loop
```js
for await (let text of fetchUrls (favoriteUrl)){
  console.log(text)
}
```
