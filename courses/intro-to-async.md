❗❗❗Links are missing

Asyncronous Programming is essentially Reactive Programming
- Reactive Programming is based on Hollywood Principle: do not call me, I will call you
  - `you give me a callback, and I will call the callback`
  - it is also considered reactive since you are not in control (like in imperative programming), but you provide callback and react when changes are made

Events and Arrays are both collections
2 Important Design Patterns are:
  1. Iterator
  2. Observer (btw this is available in ES6)
  - these 2 patterns are actually related
    - Iterator: you have a producer and a conusmer (requests info 1 at a time from producer)

Really important point,
all this methods are comparable to SQL join and select methods

how they work is slightly swapped
- since SQL is relational system (children have reference to parent) and in JS structures it is hierchical
 - parents contain children (and therefore the reference to them)


Enemy of the async programming is state
- essentially here you are not modifying existing data but rather creating new data
- this prevents many bugs which can be classified as state-bugs (e.g., some indexing problems with array)

Observables in comparison to Events can end
  - not sure what he means by this, but in the essence it is "events" like the stream which emits single instances of events
    - and "event" as such stream can't complete, but observables can
    - we can transform observables that it works like "when you fire only 1 event complete yourself"... and then when it does that it will also delete all event handlers associate it to it
- Observable is like an event and function at the same time
  - as an event in a sense that it will push you a data
  - and a function in a sense that it will do that only when you call forEach

# anatomy of observable
  - setTimeout actually gives you a handle
    - `const handle = setTimeout(some_func, 2000)` - this handle can be used to stop executing the callback if we change our mind about firing that callback, i.e., we would call `clearTimeout(handle)`
  - Observable is essentially an object with forEach method and accepts observer object (an object with `onNext`, `onComplete`, `onError` methods)
  - subscribing to observer is like subscribing to event object, the difference is that observable object gives you three callbacks instead of one (events have only `onNext()`)
  - observables wrap different push sources [push sources with different APIs] (e.g., DOM events, setTimeout, XMLHttpRequest) and adapt them so they can all be handled in the same way
  - Differences between Promises and Observables
    - Promise is something that happens only once and can not be canceled
    - Observable is a stream that can go on continiously
    - Additional difference: Observable is lazy and Promise is eager
      - observable does nothing until you call its forEach
      - on the other hand if you create Promise (it already issued a network request or something else what it does)
        - therefore, you can't retry a promise (only make a new Promise)
      - Observable is therefore a richer types, since it can do more
  - Observable should be present in ES7
  - diff between Node Streams and Observables is that Node Stream is something between Iteration and Observable (Observable only has "dispose" which stops observable) but node streams also have the option to pause the push of data for some duration
    - node stream is both push and pull


Important:
await (ES7) is just a syntactic sugar based around generators/iterators

```javascript
async function getStockPrice(name) {
  const symbol = await getStockSymbol(name);
  const price = await getStockPrice(symbol);
  return price
}
```

is same as writing a helper function in ES6

```javascript
const getStockPrice = async(function*() {
  const symbol = yield getStockSymbol(name);
  const price = yield getStockPrice(symbol);
  return price
})
```
Every Observable has 4 abilities (4 semantics):
1. to deliver value
2. to deliver error
3. to say I am completed
4. the ability for consumer to say I don't want anymore data
- most other async APIs do not have all of these abilities (e.g., fetch - network requests, can't be canceled (from the consumer))

When you are manipulating an object that you didn't create you want to use forEach
- e.g., if you want to show a form when a certain button is clicked, you will make the observable for clicks on that button and forEach (click) you will show/hide/something_else form
- when you are manipulating data structures you use other operators (map/filter/reduce) which return new objects

i.e., forEach is responsible for "side effects" in your code while other operators have the comply with functional programming
  - for certain input produce certain output (and do not change anything outside of the function)


`ConcatAll` vs `MergeAll` vs `SwitchLatest` (these are flattening patterns (they define which concurency pattern you want for these inner observables... because it is usually the case that you have an outer observable (e.g., clicks) which produces inner observables for each "event" from that observable (e.g., network requests) - and what is the right concurency pattern to flatten these innner observables))
- in Frontend most of the time is used switchLatest
- there is also `takeUntil`
- there is also `take(1)` ...check what is `take` (and how it differes from `takeUntil`)

Be careful about side-effects, it is not that you don't want them, but you should know where to place them
- in the case of observables, aim to put side-effects when you create observable, so that these side-effects are unleashed when you for-each that observable
- check `doAction()` (used to inject some additional behavior, i.e., side-effect when you forEach over observable)
  - it is for synchronous side-effects
  - it is explained here: https://frontendmasters.com/courses/asynchronous-javascript/completing-the-close-button/


forEach in observable receives as parameter an observer ... and in the execution within forEach... observable will call the callbacks of observer

The usual pattern in frontend (where observables and rxjs are handy) is you have some kind of change in ui (e.g., clicks, keypresses) and you want to make a side-effect for each "change" (e.g., issue a network request, save to db, make animation) and then you get observables which hold inner observables (for each click we get observable for network requests) and then we need to decide what is the right flattening technique (i.e., mergeAll, concatAll, switchLatest) (90% of the time in frontend it is switchLatest)
