# Reading 07

##### global and nonlocal keywords.

##### Python Scope

> scope rules how variables and names are looked up in your code.
> Python scope concept is generally presented using a rule known as the LEGB rule.

> The letters in the acronym LEGB stand for Local, Enclosing, Global, and Built-in scopes

1. What scopes are and how they work in Python

[x] scope of a name defines the area of a program in which you can unambiguously access that name, such as variables, functions, objects, and so on
[x] A name will only be visible to and accessible by the code in its scope.

> Global scope: The names that you define in this scope are available to all your code.

> Local scope: The names that you define in this scope are only available or visible to the code within the scope.

NOTE > You’ll be using the term name to refer to the identifiers of variables, constants, functions, classes, or any other object that can be assigned a name.

Linguistics note: When you can access the value of a given name from someplace in your code, you’ll say that the name is in scope. If you can’t access the name, then you’ll say that the name is out of scope

> variables in Python come into existence when you first assign them a value

> functions and classes are available after you define them using def or class, respectively

> modules exist after you import them


|Operation | Statement |
|----- | -----
|Assignments	| x = value
|Import operations	| import module or from module import name|
|Function definitions	| def my_func(): ...|
|Argument definitions in the context of functions	| def my_func(arg1, arg2,... argN): ...|
|Class definitions	| class MyClass: ...|

> All these operations create or, in the case of assignments, update new Python names because all of them assign a name to a variable, constant, function, class, instance, module, or other Python object.

> where you assign or define a name in your code determines the scope or visibility of that name

> Python scopes are implemented as dictionaries that map names to objects. These dictionaries are commonly called namespaces

2. Why it’s important to know about Python scope

3. What the LEGB rule is and how Python uses it to resolve names

> Local (or function) scope is the code block or body of any Python function or lambda expression. This Python scope contains the names that you define inside the function. These names will only be visible from the code of the function. It’s created at function call, not at function definition, so you’ll have as many different local scopes as function calls. This is true even if you call the same function multiple times, or recursively. Each call will result in a new local scope being created.

> Enclosing (or nonlocal) scope is a special scope that only exists for nested functions. If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function. This scope contains the names that you define in the enclosing function. The names in the enclosing scope are visible from the code of the inner and enclosing functions.

> Global (or module) scope is the top-most scope in a Python program, script, or module. This Python scope contains all of the names that you define at the top level of a program or a module. Names in this Python scope are visible from everywhere in your code.

##### Whenever you run a Python program or an interactive session like in the above code, the interpreter executes the code in the module or script that serves as an entry point to your program. This module or script is loaded with the special name, __main__. From this point on, you can say that your main global scope is the scope of __main__.

> inspect the names within your main global scope, you can use dir(). If you call dir() without arguments, then you’ll get the list of names that live in your current global scope.

> Built-in scope is a special Python scope that’s created or loaded whenever you run a script or open an interactive session. This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python. Names in this Python scope are also available from everywhere in your code. It’s automatically loaded by Python when you run a program or script.

note [x] if you reference a given name, then Python will look that name up sequentially in the local, enclosing, global, and built-in scope. If the name exists, then you’ll get the first occurrence of it. Otherwise, you’ll get an error.

1. Inside inner_func(): This is the local scope, but number doesn’t exist there.
2. Inside outer_func(): This is the enclosing scope, but number isn’t defined there either.
3. In the module scope: This is the global scope, and you find number there, so you can print number to the screen.

|Action |Global Code | Local Code | Nested Function Code|
|---|---|---|---
|Access or reference names that live in the global scope|Yes|Yes|Yes|
|Modify or update names that live in the global scope | Yes | No (unless declared global) | No (unless declared global) |
|Access or reference names that live in a local scope | No | Yes (its own local scope), No (other local scope) | Yes (its own local scope), No (other local scope) |
|Override names in the built-in scope | Yes | Yes (during function execution) | Yes (during function execution) |
|Access or reference names that live in their enclosing scope | N/A | N/A | Yes |
|Modify or update names that live in their enclosing scope | N/A| N/A | No (unless declared nonlocal)|

4. How to modify the standard behavior of Python scope using global and nonlocal

> Python provides two keywords that allow you to modify the content of global and nonlocal names. These two keywords are:

1. global
2. nonlocal

[x] global statement. > With this statement, you can define a list of names that are going to be treated as global names

> The statement consists of the global keyword followed by one or more names separated by commas. You can also use multiple global statements with a name (or a list of names)

> You can also use a global statement to create lazy global names by declaring them inside a function. Take a look at the following code:

``` python
>>> def create_lazy_name():
...     global lazy  # Create a global name, lazy
...     lazy = 100
...     return lazy
...
>>> create_lazy_name()
100
>>> lazy  # The name is now available in the global scope
100
>>> dir()
```
> Note: Even though you can use a global statement to create lazy global names, this can be a dangerous practice that can lead to buggy code. So, it’s best to avoid things like this in your code.

> nonlocal names can be accessed from inner functions, but not assigned or updated. If you want to modify them, then you need to use a nonlocal statement.

> The nonlocal statement consists of the nonlocal keyword followed by one or more names separated by commas.

> use nonlocal to modify a variable defined in the enclosing or nonlocal scope:

``` python
>>> def func():
...     var = 100  # A nonlocal variable
...     def nested():
...         nonlocal var  # Declare var as nonlocal
...         var += 100
...
...     nested()
...     print(var)
...
>>> func()
200
```
> Unlike global, you can’t use nonlocal outside of a nested or enclosed function

> look at the following code for an example of how closures work and how you can take advantage of them in Python:

``` python
>>> def power_factory(exp):
...     def power(base):
...         return base ** exp
...     return power
...
>>> square = power_factory(2)
>>> square(10)
100
>>> cube = power_factory(3)
>>> cube(10)
1000
>>> cube(5)
125
>>> square(15)
225
```

5. What scope-related tools Python offers and how you can use them

> When you write a Python program, you typically organize the code into several modules. For your program to work, you’ll need to bring the names in those separate modules to your __main__ module. To do that, you need to import the modules or the names explicitly

``` python
['__annotations__', '__builtins__',..., '__spec__']
>>> import sys
>>> dir()
['__annotations__', '__builtins__',..., '__spec__', 'sys']
>>> import os
>>> dir()
['__annotations__', '__builtins__',..., '__spec__', 'os', 'sys']
>>> from functools import partial
>>> dir()
['__annotations__', '__builtins__',..., '__spec__', 'os', 'partial', 'sys']
```

> You first import sys and os from the Python standard library. By calling dir() with no arguments, you can see that these modules are now available for you as names in your current global scope. This way, you can use dot notation to get access to the names that are defined in sys and os

## Videos

NOTE* The repeated Big O content is intentional. This is a big concept and worth hearing about from multiple presenters. TIP: watch on faster speed if you like.

Don’t be CONFUSED by BIG O notation anymore!

> Here is the formal mathematical definition of Big O.

Let T(n) and f(n) be two positive functions. We write T(n) ∊ O(f(n)), and say that T(n) has order of f(n), if there are positive constants M and n₀ such that T(n) ≤ M·f(n) for all n ≥ n₀.

> we are typically only interested in how fast T(n) is growing as a function of the input size n.

For example, if an algorithm increments each number in a list of length n, we might say: “This algorithm runs in O(n) time and performs O(1) work for each element”.

> A function's Big-O notation is determined by how it responds to different inputs. How much slower is it if we give it a list of 1000 things to work on instead of a list of 1 thing?

> Big-O is all about the approximate worst-case performance of doing something.

> This is a bit of a silly example, but bear with me. This function is called O(1) which is called "constant time". What this means is no matter how big our input is, it always takes the same amount of time to compute things.

> 

Bookmark/Skim

[x] Rolling Dice Examples-Done!