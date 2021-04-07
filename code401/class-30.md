# Reading: React 1

## ES6 Syntax and Feature Overview

> Note: A commonly accepted practice is to use const except in cases of loops and reassignment.

|KeyWord | Definition|
|---|---|
|Variable declaration |cannot be hoisted or redeclared.|
|Constant declaration |  cannot be redeclared or reassigned, but is not immutable.|
|Arrow function syntax | a shorter way of creating a function expression. Arrow functions do not have their own this, do not have prototypes, cannot be used for constructors, and should not be used as object methods |
|Template literals | Expressions can be embedded in template literal strings. |
|Implicit returns | The return keyword is implied and can be omitted if using arrow functions without a block body.|
|Key/property shorthand | shorter notation for assigning properties to variables of the same name.|
|Method definition shorthand | The function keyword can be omitted when assigning methods on an object.|
|Destructuring (object matching) | Use curly brackets to assign properties of an object to their own variable |
|Array iteration (looping) | A more concise syntax has been introduced for iteration through arrays and other iterable objects. |
|Default parameters | Functions can be initialized with default parameters, which will be used only if an argument is not invoked through the function |
|Spread syntax | Spread syntax can be used to expand an array. |
|Classes/constructor functions | ES6 introducess the class syntax on top of the prototype-based constructor function.|
|Inheritance | The extends keyword creates a subclass|
|Modules - export/import | Modules can be created to export and import code between files.|
|Promises/callbacks | Promises represent the completion of an asynchronous function. They can be used as an alternative to chaining functions.|

## React - Hello World
## React - JSX

> JSX produces React “elements”. 

> You can put any valid JavaScript expression inside the curly braces in JSX. 

> n the example below, we embed the result of calling a JavaScript function, formatName(user), into an ```<h1>``` element.

``` javascript
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

> After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.

>  you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions

> You may use quotes to specify string literals as attributes

> You may also use curly braces to embed a JavaScript expression in an attribute

> Since JSX is closer to JavaScript than to HTML, React DOM uses camelCase property naming convention instead of HTML attribute names.

> If a tag is empty, you may close it immediately with />

> JSX tags may contain children

> It is safe to embed user input in JSX

> Babel compiles JSX down to React.createElement() calls

## React - Rendering Elements

> An element describes what you want to see on the screen

> React elements are immutable. Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.

> React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

## React - Components & Props

> Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen

> The simplest way to define a component is to write a JavaScript function, is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element

>  elements can also represent user-defined components:

> Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail

> Don’t be afraid to split components into smaller components

> Whether you declare a component as a function or a class, it must never modify its own props

## React - State & Lifecycle

> We call ReactDOM.render() to change the rendered output:

> You can convert a function component like Clock to a class in five steps:

1. Create an ES6 class, with the same name, that extends React.Component.
2. Add a single empty method to it called render().
3. Move the body of the function into the render() method.
4. Replace props with this.props in the render() body.
5. Delete the remaining empty function declaration.

> move the date from props to state in three steps

1. Replace this.props.date with this.state.date in the render() method
2. Add a class constructor that assigns the initial this.state
3. Remove the date prop from the <Clock /> element

> There are three things you should know about setState().

1. Do Not Modify State Directly
2. State Updates May Be Asynchronous
3. State Updates are Merged

> The Data Flows Down: Neither parent nor child components can know if a certain component is stateful or stateless, and they shouldn’t care whether it is defined as a function or a class.

## React - Handling Events

> React events are named using camelCase, rather than lowercase.

> With JSX you pass a function as the event handler, rather than a string.

> This=> ```<button onclick="activateLasers()">```

> Becomes this=> ```<button onClick={activateLasers}>```

> Inside a loop, it is common to want to pass an extra parameter to an event handler.

## Utility First CSS

> Using utility classes to build custom designs without writing CSS
easily solved by extracting components
> This approach allows us to implement a completely custom component design without writing a single line of custom CSS

> The biggest maintainability concern when using a utility-first approach is managing commonly repeated utility combinations

> easily solved by extracting components

## [Tailwind in 15 minutes](https://www.youtube.com/watch?v=6zIuAyLZPH0)

A quick intro to tailwind

## Learn Next.js

>  Next.js, the React Framework

1. An intuitive page-based routing system (with support for dynamic routes)
2. Pre-rendering, both static generation (SSG) and server-side rendering (SSR) are supported on a per-page basis
3. Automatic code splitting for faster page loads
4. Client-side routing with optimized prefetching
5. Built-in CSS and Sass support, and support for any CSS-in-JS library
6. Development environment with Fast Refresh support
7. API routes to build API endpoints with Serverless Functions
7. Fully extendable

## [Why to use Next.js](https://www.youtube.com/watch?v=rtgbaKBhdkk)
