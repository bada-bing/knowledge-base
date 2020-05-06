[Advanced Vue](https://frontendmasters.com/courses/advanced-vue/)
[slides](https://docs.google.com/presentation/d/1TgDx4DN8YqfdndYWMovBcQVPWyKLTNcbo1YS8XlLo9o/edit#slide=id.g19eebb1966_0_65)

# Fundamentals
# 1. Reactivity
   - This is essentially Observer Pattern, i.e., How to make some components react to changes in other components
     - also, how should HTML react to changes in Vue Framework
   - consider an example, we have variables a and b
     - b should be a*10
     - how to implement that
     - we should update the state of variable a inside of a function so that it can also trigger the update of b
     - ```javascript
        onAChanged(() =>{
          b = a *10;
        })
        ```
  - The template (or JSX render functions), are the constructs that allow us to declare the relationship between the state and the view.
    - Put it another way, the template is the equivalent of the formula in a spreadsheet.
    ## Template Syntax
      - [Interpolation](https://vuejs.org/v2/guide/syntax.html#Interpolations)
    - [Difference between 'el' and 'template' in vue component and app - SO link](https://stackoverflow.com/questions/46596769/what-is-the-difference-between-el-and-template-in-vue-component-and-app)

    - if we would use templates (which compile into render functions) our code would look like this:
    - ```html
      <input class="cell a">
      <span class="cell b1">
        {{ state.a * 10 }}
      </span>
      ```
    - ⭐ This is the essence of Frontend Framework App is : **`view = render(state)`**
    - View can be different things: in Virtual DOM context view is a new virtual DOM tree, but more generically, think of it as applying the side effect of mutating the DOM.

    - But this is only half the picture: there is also the question of how to declaratively map user inputs to state changes?
    - In Cycle terms, that’s the half that maps User Intent to State. (That is a domain Rx is really good at) [essentially, the other direction]
    - But for now only focus on the state -> view parts.

    ```javascript
      onStateChanged(() => {
        view = render(state)
      })
      ```
    - how app knows when onStateChanged should be called / updates should be re-rendered?

    ```typescript
    let update, state
    const onStateChanged = (_update:function) => {
      //_update is function which we pass and which will be executed when state changes
      update = _update;
    }
    const setState = (newState:object) => {
      state = newState; // in the example with a and be, this would be: a = newValue
      update()          // and this would be, update b accordingly to a*10
    }
    ```


    ```javascript
    onStateChanged(() => {
      view = render(state);
    })

    setState({ a : 5})
    ```
    - This is the **pull strategy** (how is React implemented)
      - it requires that the explicit signal `(setState)` to enter a pull cycle

  Vue tracks it dependencies in order to render view
    - this is push approach (in comparison to react who epxlicitly needs to say now I am updating the state)

  - this is the basic dependency tracking systems for view updates i.e., how Vue update system works
  - in the autorun we can put jobs of different granularity (a simple calculations for computed properties, or it can be used to rerender a component)
    - this is the foundation of re-render system in Vue
  - we have observe() and autorun() which triggers re-computation from autorun when object is mutated

    - observe() is used to make an object reactive with **Object.defineProperty** (native JS Api)
      - we can use getters and setters to inform interessted components when something is changed
    - autorun() run a computation while collecting its dependencies
      - this is previous `onStateChanged` function
      - essentially this is the method of component which will add the component to the list of subscribers of that dependency..
        - and when dependency.notify() happens the component will also be informed (some of its methods will be executed)
  ```javascript
  autorun(() => {
    console.log(state.count)
  })
  ```

  - once again check part about autorun and obseve
# 2. Writing Plugins

how is plugin used: `Vue.use(plugin)`

how is constructed:
```javascript
function (Vue, options) {
  // ...plugin code
}
```

globally applied mixin essentially works as a plugin, but plugin has some better features so use plugins instead of mixin
`Vue.mixin(options)`
- mixins are snippets of reusable component options that can be mixed into components
- plugins are automatically deduped, i.e., deduplicated (and vue-mixins do not do that)
  - if you have multiple calls to the same plugin, it will prevent it from being applied over and over again

Vue instance has the not well known feature `$options` (this.$options)
  - contains merged normalized options object of that specific instance
  - options can come from different places (from global mixins, from component own definition, or from inheritance, ...)
  - contains both native and custom options


3. Render Functions
render functions of most frontend frameworks use h as a default name for the callback function because the end results of these functions is something like hyperscript (this was the original implementation) i.e,. https://github.com/hyperhype/hyperscript

# State Management
dispatch triggers an action, and commit triggers a mutation
	- [nice detailed answer [SO]](https://stackoverflow.com/questions/40390411/vuex-2-0-dispatch-versus-commit/40393742#40393742)


# Routing
Vue Router
  - [official docs](https://router.vuejs.org/)
  - [getting started](https://scotch.io/tutorials/getting-started-with-vue-router)
- route params - part of the URL which are dynamically determined
	- e.g., /user/:id
- query params - params which come after the question mark
	- e.g., /user?lang=en-DE
-⭐ https://vueschool.io/articles/vuejs-tutorials/make-router-vue-js-plugin/

# Future
https://css-tricks.com/guides/vue/

# Syntax
[Vue Class Component](https://class-component.vuejs.org/) & [Vue Property Decorator](https://github.com/kaorun343/vue-property-decorator)
- @Component Decorator (class properties are data and methods are methods, @Prop and @Watch)
- This syntax enables class inheritance and usage of decorators
