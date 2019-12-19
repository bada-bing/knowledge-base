# Other #
- [TS PROJECT](./ts_project.md)
- [Mike - TS Intro V2 Frontend Masters](./ts_frontend_masters.md)

*** NOTE: *** I suppose that in order to use TS in cart-ui we need to provide some plugin/compiler to Webpack but check that!
*tsc* - TS Compiler
ts-node is used to run typescript directly (?)

TS Compiler
- use nightly version because the compiler catches more and more bugs as it progresses

2 Goals of TS
- Optional Type System
    - add types to JS to include code quality and understandabilty
    - provides compile-time type safety for JS code
    - TS is only a superset of JS with optional Type checking
        - "TS is just JS with docs" (it is essentially linting JS using type info)
        - types can be considered as additional documentation which is understandable by compiler
- Provide planned features from future(next) JS editions to current JS engines


Types
- can be inferred (e.g., TS knows that 123 is number) or explicit (var foo: number = 123)
- Types are structural
- Type errors do not prevent JS emit (you can still execute the code even though it has type errors)
- Types can be ambient - Decoration
- https://github.com/DefinitelyTyped/DefinitelyTyped

Additional Info about Types (I suppose this relates to keywords in language):
1. Classes - Class
1. Inheritance - extends
1. Static members (methods and properties) - static
1. Access modifiers - public, private, protected
1. Abstract - abstract
1. Type alias - type

Equality
- always use === except for null-checks (in that case you often want ==)
    - in TS: *string == number* gives a TS error
- Structural Equality

Null & Undefined
- Something has not been initialized: undefined
- Something is currently unavailable: null

TS Compiler inserts 'strict' mode for you if you use modules

### Files ###
*tsconfig*
Open Questions:
- module vs target?
- why do we use: esnext?
- moduleResolution vs module

*source decalaration files* *- **.d.ts***
- declare class …
- interface Example …
- [About d.ts files](https://stackoverflow.com/questions/21247278/about-d-ts-in-typescript) [SO]
- The "d.ts" file is used to provide typescript type information about an API that's written in JavaScript. The idea is that you're using something like jQuery or underscore, an existing javascript library. You want to consume those from your typescript code. Rather than rewriting jquery or underscore or whatever in typescript, you can instead write the d.ts file, which contains only the type annotations. Then from your typescript code you get the typescript benefits of static type checking while still using a pure JS library.
- A large collection of .d.ts files can be found at "definetly typed" (@types/…)

https://blog.angular-university.io/typescript-2-type-system-how-do-type-definitions-work-in-npm-when-to-use-types-and-why-what-are-compiler-opt-in-types/


## Types ##
- [TS Type System](https://basarat.gitbooks.io/typescript/content/docs/types/type-system.html)
- Interfaces
    - common solution to compose multiple annotations into a single one
- any
- null (compiler flag: strictNullChecks), undefined, void
- Generics (e.g., Array<T>)
- Union (type1|type2) and Intersection (type1 & type2)
- Tuple type - [type1, type2]
    - boolean[] - array of booleans
    - [boolean, boolean] - tuple of booleans

	- string[] is same as Array<string>
	- Optional Fields are marked with Question mark
	- Non-Null Fields are marked with Exclamation point
	- Union type: string | number



- [About interfaces](https://blog.logrocket.com/interfaces-in-typescript-what-are-they-and-how-do-we-use-them-befbc69b38b3/)

- Just like values bigger than Number.MAX_VALUE get clamped to INFINITY, values smaller than Number.MIN_VALUE get clamped to 0.

TIP: !!variable => converts variable to its boolean value (true or false)


### Other ###
- https://medium.com/javascript-in-plain-english/typescript-with-node-and-express-js-why-when-and-how-eb6bc73edd5d
- https://www.valentinog.com/blog/typescript/