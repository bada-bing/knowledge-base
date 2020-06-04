[slides and resources](https://github.com/sdras/intro-to-vue)
[slides](https://slides.com/sdrasner/intro-to-vue-7?token=u9qUgRsW) # pass should be `!vue!`
[Intro to Vue](https://frontendmasters.com/courses/vue/)

⭐ Essentialy, the Web Frameworks such as Vue compile HTML and populate with the data which is specified in JS framework

❗ Conventions & Best-Practices:
	- How to name components: kebab-case
	- Rest API Consumption - Ajax Requests: Axios

Vue Important Topics
- [Virtual DOM](https://bitsofco.de/understanding-the-virtual-dom/)
- [Global Event Bus](https://alligator.io/vuejs/global-event-bus/)
- [Reactivity in Vue.js](https://medium.com/js-dojo/reactivity-in-vue-js-and-its-pitfalls-de07a29c9407)

# Directives:
  [VueJS Docs - Directives](https://vuejs.org/v2/guide/syntax.html#Directives)
  [link](http://slides.com/sdrasner/intro-to-vue-1?token=9-aFNhlX)

- Directives are put on the elements in HTML markup (e.g., v-on)
- you can create custom directives (each directive has 5 hooks)

## Model binding
- `v-bind`: dynamic (one-way) binding (shorthand version `:`)
- [SO diff v-model and v-bind](https://stackoverflow.com/questions/42260233/vue-js-difference-between-v-model-and-v-bind)
  - essentially, v-bind is one way binding (from vue-framework to html) and v-model is 2-way binding
- `v-on`: opposite of `v-bind`, binds events from HTML to vue-framework (shorthand version `@`)
  - the event-handlers receive automatically as a parameter event `e` which triggered them
  - multiple bindings on one element are allowed
  - ```
    <div v-on="
      click  : onClick,
      keyUp  : onKeyup,
      keyDown: onKeydown
    ">
    </div>```
  - use modifiers to change default behavior: e.g.,
    - `@click.once` this event will be triggered once
    - `@mousemove.stop` is comparable to `e.stopPropagation()`
    - `@mousemove.prevent` is comparable to `e.preventDefault()`
    - `@submit.prevent` will no longer reload page on submission
    - `@click.native` to listen to native events in DOM
- `v-model`: 2-way binding,
  - i.e., creates the relation between data in the (Vue) instance/component and a (HTML) form input (to dynamically update values)
  - v-model is essentially the same as:
  - ```html
    <input
      v-bind:value="some_model"
      v-on:input="some_model = $event.target.value"
      ...
    />
    ```
- [Modifiers](https://vuejs.org/v2/guide/syntax.html#Modifiers) of directives, e.g., for v-on and v-model
  - e.g., prevent for `event.preventDefault`
  - v-model.*trim* will strip any leading or trailing whitespace from the bound string
  - v-model.*nubmer* will change strings to number inputs
  - v-model.*bind* ???
  - v-model.lazy="some_property"
    - `<input v-model.lazy="some_property"/>`
    - the some_property is not updated on every change (every key stroke) but it is updated when we lose focus from the input (when we change focus to the other input or part of the screen)

## List Rendering
  - v-for
  - [Array Change Detection](https://vuejs.org/v2/guide/list.html#Array-Change-Detection)

## Conditional Rendering
  - v-if/v-else/v-else-if
  - v-if/v-show
  - ❗ `v-if` has higher toggle costs while `v-show` has higher initial render costs. So prefer `v-show` if you need to toggle something very often, and prefer `v-if` if the condition is unlikely to change at runtime
  - [Controlling Reusable Elements with key](https://vuejs.org/v2/guide/conditional.html#Controlling-Reusable-Elements-with-key)
    - e.g., reusing same input element for different use-cases
- ❓ v-html - for strings that have html which need to be rendered
- v-pre (prints out the inner text exactly as it is (including code), good for docs)
  - skip compiling for raw content, can boost performance
  - ❓ you can use <pre> tag for that directive
- v-once (only once renders the content)

# Instance Methods, Computed, Watchers, Data
[link](http://slides.com/sdrasner/intro-to-vue-2?token=502n2b7V)
- **Methods**: bound to Vue instance/component; can be accessed in directives (in HTML/templates)
  - have the access to the component/instance through `this` keyword
  - ❗ usually, the main goal is to invoke them from `v-on` directives
- **Computed**: calculations that are cached and updated only when needed, i.e., **when dependencies change**
  - computed should be used as property (in place of `data`); they provide a different view on some data
  - `computed` run only when a dep has changed | `methods` run whenever an update occurs (i.e., everytime when `render` function is called)
  - A computed property will only re-evaluate its value when some of its reactive dependencies have changed.
  - computed by default have only getters (but you can define setters if necessary)
- [**Watchers**](https://vuejs.org/v2/guide/computed.html) & Vue's Reactivity System
  - watch - $watch (the callback will be called when the related property changes)
    - [How to watch deep-data structures in Vue](https://michaelnthiessen.com/how-to-watch-nested-data-vue/)
  - **Reactive Programming** - programming with asynchronous data streams
    - Stream - a sequence of **ongoing events ordered in time** on which you can attach **hooks** to observe it
    - When we use **reactive premises** for building apps, this means that **it is very easy to update state in reaction to events**
    - ⭐[The Intro to Reactive Programming](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754)
  - In Vue reactivity is based on getters/setters, i.e., JS `Object.define` API
    - https://vuejs.org/v2/guide/reactivity.html
    - https://www.monterail.com/blog/2016/how-to-build-a-reactive-engine-in-javascript-part-1-observable-objects
    - Reactivity is based on "push"
      - React is not reactive in that sense, since it is using "pull" and not "push"

# How Vue works
  - the framwork goes through defined properties and converts them to be reactive (using `Object.define()`)
  - Vue can not detect at later points properties addition/deletion so we need to keep track on them in dedicated objects
    - e.g., data:
    ```js
    {
      some_property
    }
    ```
  - ⭐ The process:
    - Each component has a watcher instance
    - The properties touched by watcher during the render are registered as dependencies
      - When the setter is triggered, it lets the watcher know, and causes the component to re-render.
  - The Vue instance is the middleman between DOM and business logic
    - watchers update DOM only when necessary
      - accessing DOM is not perfomrant as executing JS
      - therefore we use virtual DOM, which is a copy of DOM which exists in JS
      - instead of rerendering the whole DOM it will only update differencies

# Components
[link](http://slides.com/sdrasner/intro-to-vue-3?token=LwIVIblm)
[Vue DOC - Components](https://vuejs.org/v2/guide/components.html)
⭐ Vue uses HTML-based template syntax to bind the Vue instance to DOM
- templates are optional; layer above `render` functions (which also support JSX syntax)

Component - a collection of elements encapsulated into a group that can be accessed through one single interface
- [Component Registration](https://vuejs.org/v2/guide/components-registration.html) - Globally vs Locally
    - Globally (across whole Vue instance) - `Vue.component('tag_name', Object)`
    - Locally (inside of a certain component) - `components: {...}`
    - both approaches can be used for Components, Filters, Mixins, etc…
- ❗ If a component and the Vue instance are in the same file, you don't need to register it (check example below)
- Each component has its own isolated scope
  - therefore, data must be a function `data() { return { text="miki" } }`
- CamelCase is converted to kebab-case:
  - `props: ['booleanValue']` vs `<some-component :boolean-value='booleanValue'></some-component>`
- **EXAMPLE_1**: The following example includes HTML and JS:
```javascript
  Vue.component('child', {
    props: {text: {
      type: [String, Number],
      required: true,
      default: "no-value"
      },
    template: `<div>{{ text }}</div>`
  });

  new Vue({
    el: #app,
    data() {
      return {
        message: "hello mr. magoo"
      }
    }
  })
```
```html
<div id="app">
  <child :text="message"></child>
</div>
```
## Dynamic Rendering/Loading of Components
- `<component :is="">` : dynamically determine which component to load
- you can use it statically like this: <li is='individual-comment'>
	- uses binding with :is
		- `<component :is="some_data_property"></component>`
		- This loads the component based on the value of some some_data_property
			- the value should be equal to the selector of a certain component in order to be loaded
			- Once you have selected certain component and then the value of some_data_property changes and new component is loaded (the old one will be destroyed)
			- you can override this behavior by wrapping the component inside of <keep-alive> tag
				- in that case the component instead of destroyed lifecycle hook it has new hooks
					- deactivated and activated

# [Instance Properties](https://vuejs.org/v2/api/#Instance-Properties)
- **Props**: used to pass the data (i.e., properties) from the parent to child components/elements (1-way communication)
  - ❓ when props is a type of `Object` or `Array` it needs to return value from a function
  - if you use props without `:` (v-bind) essentially you are providing a static value to the component which receives that props
    - `<child text="3"></child>`
  - therefore, you use v-bind (:) to dynamically bind props to data on the parent

- **Events** - opposite way of communication to props is emitting/communicating events
- $emit - the child is reporting it's activity to the parent (like props 1-way communication, just in the other direction)
  - in child: `this.$emit('my-event', eventValue, eventValueTwo);`
  - in parent: <template> ... <child @my-event='customEventHandler'> ... <template>
- [Custom Events](https://vuejs.org/v2/guide/components-custom-events.html)
  - ❗ always use kebab-case for event names
- [Programmatic Event Listeners](https://vuejs.org/v2/guide/components-edge-cases.html#Programmatic-Event-Listeners)

- **Slots** - use them to customize the child components from the outside
  - parent provides some implementation details to the child in the parts which are labeled as slots
  - in child: `<slot name='headerinfo'></slot>`
  - in parent: `<h1 slot="headerinfo">This populates the headerinfo slot</h1>`
  -  embed HTML markup into the child component
	- Used when you want to embed a certain HTML code into the child component (and pass it from the parent component)
	- When compiling the template code all data manipulation (like interpolation {{..}}) is done in the parent component
		- it will take everything (which is dynamically determined) from the parent component
			- styling and data interpolation
	- https://adamwathan.me/the-trick-to-understanding-scoped-slots-in-vuejs/
	- https://alligator.io/vuejs/scoped-component-slots/

- Lifecycle Hooks: https://scotch.io/tutorials/demystifying-vue-lifecycle-methods

# Forms
- [VeeValidate](https://logaretm.github.io/vee-validate/) - to validate the input of HTML input fields and Vue Components
- [Vue Form validation with Vuelidate](https://vuejsdevelopers.com/2018/08/27/vue-js-form-handling-vuelidate/)

# Vue CLI & Nuxt

2 Versions of Vue.js:
1. has included compiler
2. without included compiler - with VUE CLI [@vue.cli Guide](https://cli.vuejs.org/guide/)
- templates are compiled during the build process
- Build Processes (Vue CLI - layer above webpack) which enables us to use features loike ES6, SCSS...
  - Built on top of webpack and webpack-dev-server
  - enables pre-compilation (and with it VUE files - single file templates)
  - enables lazy load and async (not to load everything at startup)
  - server-side rendering, code-splitting, performance metrics, ...
  - different versions (i.e., build vs prod versions)

Base Configuration for a Vue CLI 3 project includes `webpack` and `Babel`
- and `yorkie`, used for Git hooks (based on gitHooks field in package.json)

## CLI Plugins
- npm packages that provide optional features to Vue CLI projects (e.g., Babel, ESLint...)
- `vue-cli-service`  binary automatically resolves and loads all plugins listed in the package.json file
- official plugins start with `@vue/cli-plugin-`
  - e.g., Typescript, PWA, Vuex, Vue Router, ESLint, Unit testing
- community plugins start with "vue-cli-plugin-"

- in single file templates in `style` tag you can specify:
  ```<style scoped></style>``` to apply the styles only to that component

- Important Commands:
  `vue create`	create a new project
  `vue add some-plugin`	add plugins to existing project
  `vue serve`	same as "npm run serve"
  `vue build`	same as "npm run build"
  - `vue-cli-service build`	produces a production-ready bundle in the `dist/` directory
    - with minification for JS/CSS/HTML and auto vendor chunk splitting for better caching
  `vue inspect`
  `vue ui` use GUI

- [Modes and ENV Variables](https://cli.vuejs.org/guide/mode-and-env.html#modes)
- Most important Environment Variables
	1. VUE_APP_*
	2. NODE_ENV
	3. BASE_URL
- When running vue-cli-service, environment variables are loaded from corresponding files
	- Then `NODE_ENV` will determine the primary mode your app is running in - `development`, `production` or `test` - and consequently, what kind of webpack config will be created.

Nuxt - provides:
- Automatic Code Splitting
- Server Side Rendering
- Powerful Routing System with Asynchronous Data
- Static File Serving
- ES6/7 Transpilation
- ❓ Hot reloading in Development, Pre-processors, Write Vue files...

Skipping Animations for now...
http://slides.com/sdrasner/intro-to-vue-5?token=5zRhIuNg
https://slides.com/sdrasner/animating-vue-35/

# Filters, Mixins, Custom Directives
- **mixins** sharing the common part between different components (functionality, data, props)
- Mixins is the part of the code which we can embed into our components
	- e.g., we can embed data and computed and props... but we can also embed lifecycle methods
	- Vue tries to merge both its own stuff of the component and the stuff from mixins
		- e.g., it executes both lifecycle hooks from the mixin and the one from the component
  - allow to encapsulate one piece of functionality so that you can use it in different components in the application
  - mixins should be pure (as much as possible be written using FP paradigm)
    - should not modify things outside of the function scope (so you will reliably receive the same values with the same inputs on every execution)
  - How is component merged with mixins:
    - by default, mixins are applied first and the component second (so that we can override something if necessary), ie., the component has the last say
  - Special Case: Global Mixin(added to each component in the application!)
  - Global Mixins are literally applied to every component (this should be extremly rare use-case)
    - that makes them essentially plugins
      - therefore you should use plugins, check in You's course on Vue about that
    - https://vuejs.org/v2/guide/plugins.html

- **filters** transform what the user sees (they DO NOT transform the data!)
  - they are not replacement for methods, computed or watchers
  - as other stuff you can register them globally and locally
    - globally: `Vue.filter(...)` | locally: `filters: { filterName(value) { return ...}}`
  - used in moustache-templates like this `{{ data | filter }}`
    - you can chain them `{{ data | filter1 | filter2 }}` or pass arguments `{{ data | filter(arg1, arg2) }}`
  - Filters are rerun on every single update, so better is to use **computed** for values like these that should be cached
		- computed are better because of performance reasons (Vue doesnt know when to run filter, so it runs it always, while computed property are only runned when change into the base property (computed property is changed based on base property)
 - https://scotch.io/tutorials/how-to-create-filters-in-vuejs-with-examples

- **custom-directives**
  ```javascript
  Vue.directive('track', {
      bind(el, binding, vnode) {
        //some change to element
        el.style.position = 'fixed'
      }
    });
  ```
   -  binding is the data which we pass in the template
      -  we can provide event objects there `<p v-track='{top:10, left:20}'>`
  - used in template: `<p v-track>this is now paragraph with custom directive</p>`
  - 3 Options:
    - v-example: without arguments (some functionality turned on/off on DOM elements)
    - v-example="value" pass value to directive
      - v-example=" 'string ' " use string as an expression
        - `<p v-html="'<strong>an example of a string in text</strong>'"></p>`
    - v-example:arg='value' pass an (named) argument to directive
      - `<div v-bind:class="someClassObject"></div>`
      - v-example:arg.modifier="value" - allows to use modifier
        - `<button v-on:submit.prevent="onSubmit"></button>`


# Vuex
[link](https://slides.com/sdrasner/intro-to-vue-7?token=u9qUgRsW)
- Centralized store for shared data and logic (even shared methods or async)
- unidirectional data flow (influenced by Flux application architecture)

Vuex is plugin and as every plugin requires:
In **store.js** file
  ```javascript
  import Vue from 'vue';
  import Vuex from 'vuex';
  Vue.use(Vuex);
  ```

  ```javascript
  export const store = new Vuex.store({
    state: {
      key: value
    }
  })
  ```

Vuex store has:
* getters - getters can read the value, but not mutate the state.
* mutations - update(mutating) the state, but they will **always be synchronous**. Mutations are the only way to change data in the state in the store.
* actions - allow us to update the state, asynchronously, but will use an existing mutation.
  * This can be very helpful if you need to perform a few different mutations at once in a particular order, or reach out to a server.
  * https://stackoverflow.com/questions/39299042/vuex-action-vs-mutations

Mutations vs Actions
- Actions commit Mutations
- Actions can contain asynchronous operations (an api call which result will be commited in a mutation)
- Mutations are intended to be **synchronous pure functions**
	- to receive input only via their payload and not to produce side effects elsewhere.
  	- ⭐ While actions get a **full context** to work with, mutations only have the **state and the payload**
  	- i.e., they should perform their job without request to getters

Benefits of Actions
- Actions are a very open, logical layer; there’s nothing done in actions that couldn’t be done outside the store, simply that actions are centralized in the store.
- Differences between actions and any kind of function you might declare outside of the store:
  - Actions can be scoped to a module, both when dispatching them and also in the context they have available
  - can be intercepted via `subscribeAction` API
  - Actions are promised by default, in much the same way as any async function is
- Traceability - with Vue devtools, it is possible to see a clear chronology of mutations applied to the single global state.

On the component, we would use **computed** for getters and methods to call actions (using dispatch) and mutations (using commit)
```javascript
computed: {
  value() {
    return this.$store.getters.tripleCounter;
  }
},
methods: {
  increment() {
    this.$store.commit('increment', 2)
  },
  asyncIncrement() {
    this.$store.dispatch('asyncIncrement', 2)
  }
}
```

When working with actions we need to pass in the context (contains store, getters, ...)
```javascript
actions: {
  increment (context) {
    context.commit('increment') // we are commiting a mutation called 'increment'
  }
}
```
often used simplified form
```javascript
actions: {
  increment ({ commit }) {
    commit('increment')
  }
}
```
in methods of a component `actions` are called like this:
```javascript
methods: {
  asyncIncrement() {
    this.$store.dispatch('increment'); //we are calling the action defined in store
  }
}
```
apart from context we can pass data to mutations...
```javascript
actions: {
  increment ({ commit }, data) {
    // do something with data and commit
    commit('increment', data);
  }
}
```
you can check something in Vuex called `mapActions` - to map mutations to actions

Once you finish everything check following articles:
https://alligator.io/vuejs/typescript-class-components/
https://www.freecodecamp.org/news/common-mistakes-to-avoid-while-working-with-vue-js-10e0b130925b/
https://vuejsdevelopers.com/2018/06/18/vue-components-play-nicely/
https://michaelnthiessen.com/26-time-saving-tips/

Alternatives to Vue
	- [React vs Angular](https://www.sitepoint.com/react-vs-angular/)
	- [React, redux and JS architecture](https://jrsinclair.com/articles/2018/react-redux-javascript-architecture/#fn:2)
		- React (and Vue) separates state from View
Redux seprates what happened from what we do about it
