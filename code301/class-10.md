# Read: 10 - The Call Stack and Debugging

## The Call Stack defined on MDN

> A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions
1. When a script calls a function, the interpreter adds it to the call stack and then starts carrying out the function.
2. Any functions that are called by that function are added to the call stack further up, and run where their calls are reached.
3. When the current function is finished, the interpreter takes it off the stack and resumes execution where it left off in the last code listing.
4. If the stack takes up more space than it had assigned to it, it results in a "stack overflow" error.

```
function greeting() {
   // [1] Some codes here
   sayHi();
   // [2] Some codes here
}
function sayHi() {
   return "Hi!";
}

// Invoke the `greeting` function
greeting();

// [3] Some codes here
```

The code above would be executed like this:

1. Ignore all functions, until it reaches the greeting() function invocation.
2. Add the greeting() function to the call stack list.
> Call stack list:
> greeting

3. Execute all lines of code inside the greeting() function.
4. Get to the sayHi() function invocation.
5. Add the sayHi() function to the call stack list.
> Call stack list:
> sayHi
> greeting

6. Execute all lines of code inside the sayHi() function, until reaches its end.
7. Return execution to the line that invoked sayHi() and continue executing the rest of the greeting() function.
8. Delete the sayHi() function from our call stack list.
> Call stack list:
> greeting

9. When everything inside the greeting() function has been executed, return to its invoking line to continue executing the rest of the JS code.
10. Delete the greeting() function from the call stack list.
> Call stack list:
> EMPTY

## Understanding the JavaScript Call Stack

> The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack. The browser provides web APIs like the DOM, AJAX, and Timers

1. What is it?

> At the most basic level, a call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call)

> Let us take a look at a code sample to demonstrate LIFO by printing a stack trace error to the console.
```
function firstFunction(){
  throw new Error('Stack Trace Error');
}

function secondFunction(){
  firstFunction();
}

function thirdFunction(){
  secondFunction();
}

thirdFunction();
```
> When the code is run, we get an error. A stack is printed showing how the functions are stack on top each other. Take a look at the diagram.

> Temporarily store: 
When a function is invoked (called), the function, its parameters, and variables are pushed into the call stack to form a stack frame. This stack frame is a memory location in the stack. The memory is cleared when the function returns as it is pop out of the stack.

> Manage function invocation (call):
 The call stack maintains a record of the position of each stack frame. It knows the next function to be executed (and will remove it after execution). This is what makes code execution in JavaScript synchronous.

 > A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.

Here is an example:
```
function callMyself(){
  callMyself();
}

callMyself();
```
The callMyself() will run until the browser throws a “Maximum call size exceeded”. And that is a stack overflow.

> The key takeaways from the call stack are:
1. It is single-threaded. Meaning it can only do one thing at a time.
2. Code execution is synchronous.
3. A function invocation creates a stack frame that occupies a temporary memory.
4. It works as a LIFO — Last In, First Out data structure.

## JavaScript error messages

> Most of your time as a developer is spent reading code followed by debugging that same code, most likely to be able to read it or solve an “unexpected feature”

> Types of error messages

1. Reference errors
This is as simple as when you try to use a variable that is not yet declared you get this type os errors.
```
console.log(foo) // Uncaught ReferenceError: foo is not defined
```
2. Syntax errors
> this occurs when you have something that cannot be parsed in terms of syntax, like when you try to parse an invalid object using JSON.parse.
```
JSON.parse( {'foo': 'bar'} ) // Uncaught SyntaxError: Unexpected token o in JSON at position 1
```
> This can be solved by just fixing the syntax, in this case the object should be a JSON.
```
JSON.parse('{"foo":"bar"}')
```

3. Range errors
> Try to manipulate an object with some kind of length and give it an invalid length and this kind of errors will show up.
```
var foo= []
foo.length = foo.length -1 // Uncaught RangeError: Invalid array length
```

4. Type errors
> Like the name indicates, this types of errors show up when the types (number, string and so on) you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.
```
var foo = {}
foo.bar // undefined
foo.bar.baz // Uncaught TypeError: Cannot read property 'baz' of undefined
```

##### Debugging:
> To debug your JS code, the easiest and maybe the most common way its to simply console.log() the variables you want to check or, by using chrome developer tools, open your page with your JS code (press cmd+o in macOS or Ctrl+o in Windows) and choose your file to debug, click the line you wanna debug and refresh your page again (F5)

> You can also add conditional breakpoints by right-clicking a previous set breakpoint, which will make your program stop at that point only if a condition is met

##### Call stack
> the path that your program has taken to reach the point were you set a breaking point or were you have an error

1. testing is automatically called since it’s an IIFE (immediately Invoked Function Expression);
2. obj variable is declared with the function add (using ES6 shorthand for functions in objects, it would be the same having var obj = { add: add } ;
3. the function add is called from the obj variable with two strings has parameters, there are added which makes them “12” in this scenario and then split is called before returning [“1”, “2”];
4. the function add is called again, this time with number, the values are added making it 3 but then, split (which is not available for number type variables) is called which makes an error being thrown;

##### Tools to avoid runtime errors

> quokka to evaluate your code as you type
> eslint to make sure your style guide is consistency and it will grab you an error or two along the way and
> For those of you looking to make JS a more strong typed experience you can check out stuff like TypeScript (like I said in a previous article, when learning I rather avoid libraries that abstract the core language so I wouldn’t recommend this last one when starting).


