# From the Duckett JS book:
# JavaScript book, Ch. 10

## “Error Handling & Debugging”

* This chapter is to help you *learn to find errors in your code* and it will teach you *how to write scripts that deal with potential errors gracefully*

*Things to be aware of*
1. order of execution: to find the source of an error you need to know how they are executed
2. execution contexts: there is one global execution context, plus each function creates a new execution context
3. the stack: javascript interpretor processes on line of code at a time, when statement needs data from another function, it stacks the new function ontop of the current task.
4. execution context and hoisting: two phases of activity when a script enters a new context: prepare and execute
5. understanding scope: each execution context holds its own variable object.
6. understanding errors: when javascript generates an error it throws an exception
7. error objects: can help you find where your mistakes are

> browser have these in the dev tools!

##### If you understand the two stages of execution contexts, and stacks, you are more likely to find the error in your code

> debugging is the process of finding errors in code... we've been doing this since day one!
> the console can help you narror down where the error is
> there are seven different types of errors in javascript
> If you know that you may get an error you can use the *try, catch, finally statement* to give your user healful feedback
