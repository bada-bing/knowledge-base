From Mike's Lecture (Frontend Masters)
- TS comes in 3 parts: Language, Language Server and Compiler
- TS is closely related to JSDoc comments
- Type declaration provides some sort of contract (what this variable provides) therefore it is recommended to be explicit as much as possible (and provide types, instead of letting compiler to infer it automatically)
	- types serve like documentation as well
- any is most generic type (accepts anything), opposite of any is "never"
- you specify an array with any[]
- typescript supports tuples but be careful
	- you get type safety regarding members and their types (e.g., if the certain el belongs to a type) but you don’t get type safety when you call some array methods on that tuple
        - you can push unallowed elements to a tuple and it will not complain


In general Interface is the shape of something (most of the time of a complex object), while type is in general just an alias for a custom type

TIP: Because an ideal property of software is being open to extension, you should always use an interface over a type alias if possible.

### Interface ###
- it is also a custom TS type
TIP: it is a good idea to prefix interfaces with a capital I, that’s a convention in TypeScript
	- Interfaces are extandable
		○ extend keyword

Check Type Conversions keyword "as"
const user = {…} as 
Optional Chaining in TypeScript
User


Check Type Conversions keyword "as"
const user = {…} as 
[Optional Chaining in TypeScript & VS Code](https://itnext.io/javascript-optional-chaining-just-arrived-in-vs-code-87d8a0036a0d)
User
