# Reading: React 2

## React - Conditional Rendering

>  Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them.

> You can use variables to store elements. This can help you conditionally render a part of the component while the rest of the output doesn’t change

> You may embed expressions in JSX by wrapping them in curly braces

>  in JavaScript, true && expression always evaluates to expression, and false && expression always evaluates to false.

> Therefore, if the condition is true, the element right after && will appear in the output. If it is false, React will ignore and skip it.

> Another method for conditionally rendering elements inline is to use the JavaScript conditional operator condition ? true : false.

## React - Lists & Keys

> You can build collections of elements and include them in JSX using curly braces {}.

> Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity

>  don’t recommend using indexes for keys if the order of items may change. This can negatively impact performance and may cause issues with component state.

## React - Forms

> HTML form elements work a little bit differently from other DOM elements in React, because form elements naturally keep some internal state.

> the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a “controlled component”

> When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name

## React - Lifting State

> several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancestor.

> In React, sharing state is accomplished by moving it up to the closest common ancestor of the components that need it. This is called “lifting state up”

> There should be a single “source of truth” for any data that changes in a React application.

## React - Composition vs Inheritance

> Some components don’t know their children ahead of time. This is especially common for components like Sidebar or Dialog that represent generic “boxes”.

> such components use the special children prop to pass children elements directly into their output:

> Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way

## Thinking in React

> One of the many great parts of React is how it makes you think about apps as you build them.
