# Reading 04

## Classes and Objects

Classes start with a capital letter. like this:

```python
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")

myobjectx = MyClass()
```

> to access variable:

```python
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")

myobjectx = MyClass()

myobjectx.variable
```

> create multiple different objects that are of the same class(have the same variables and functions defined). However, each object contains independent copies of the variables defined in the class

```python
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")

myobjectx = MyClass()
myobjecty = MyClass()

myobjecty.variable = "yackity"

# Then print out both values
print(myobjectx.variable)
print(myobjecty.variable)
```

> to access a function inside of an object you use notation similar to accessing a variable:

```python
class MyClass:
    variable = "blah"

    def function(self):
        print("This is a message inside the class.")

myobjectx = MyClass()

myobjectx.function()
```

## Thinking Recursively

> The algorithm for iterative present delivery implemented in Python:

```python
houses = ["Eric's house", "Kenny's house", "Kyle's house", "Stan's house"]

def deliver_presents_iteratively():
    for house in houses:
        print("Delivering presents to", house)
```

> The algorithm for recursive present delivery implemented in Python:

```python
houses = ["Eric's house", "Kenny's house", "Kyle's house", "Stan's house"]

# Each function call represents an elf doing his work 
def deliver_presents_recursively(houses):
    # Worker elf doing his work
    if len(houses) == 1:
        house = houses[0]
        print("Delivering presents to", house)

    # Manager elf doing his work
    else:
        mid = len(houses) // 2
        first_half = houses[:mid]
        second_half = houses[mid:]

        # Divides his work among two elves
        deliver_presents_recursively(first_half)
        deliver_presents_recursively(second_half)
 
>>> deliver_presents_recursively(houses)
Delivering presents to Eric's house
Delivering presents to Kenny's house
Delivering presents to Kyle's house
Delivering presents to Stan's house
```

> When dealing with recursive functions, keep in mind that each recursive call has its own execution context, so to maintain state during recursion you have to either:

1. Thread the state through each recursive call so that the current state is part of the current call’s execution context
2. Keep the state in global scope

> The state that we have to maintain is (current number we are adding, accumulated sum till now).

Here’s how you do that by threading it through each recursive call (i.e. passing the updated current state to each recursive call as arguments):

```python
def sum_recursive(current_number, accumulated_sum):
    # Base case
    # Return the final state
    if current_number == 11:
        return accumulated_sum

    # Recursive case
    # Thread the state through the recursive call
    else:
        return sum_recursive(current_number + 1, accumulated_sum + current_number)
 
# Pass the initial state
>>> sum_recursive(1, 0)
55

```

> Here’s how you maintain the state by keeping it in global scope:

```python
# Global mutable state
current_number = 1
accumulated_sum = 0


def sum_recursive():
    global current_number
    global accumulated_sum
    # Base case
    if current_number == 11:
        return accumulated_sum
    # Recursive case
    else:
        accumulated_sum = accumulated_sum + current_number
        current_number = current_number + 1
        return sum_recursive()
 
>>> sum_recursive()
55
```

> Python doesn’t have support for tail-call elimination. As a result, you can cause a stack overflow if you end up using more stack frames than the default call stack depth:

```python
>>> import sys
>>> sys.getrecursionlimit()
3000
```

> nice joke: I was once asked to explain recursion in an interview. I took a sheet of paper and wrote Please turn over on both sides.

> Recursion can also be seen as self-referential function composition. We apply a function to an argument, then pass that result on as an argument to a second application of the same function, and so on. Repeatedly composing attach_head with itself is the same as attach_head calling itself repeatedly.

## Pytest Fixtures and Coverage

> fixtures = you'll want to have some objects available to all of your tests. Those objects might contain data you want to share across tests, or they might involve the network or filesystem.

> In pytest, you define fixtures using a combination of the pytest.fixture decorator, along with a function definition.

```python
def reverse_lines(f):
   return [one_line.rstrip()[::-1] + '\n'
           for one_line in f]
```

> in reference to test coverages:
> there's a package called pytest-cov on PyPI that you can download and install. Once that's done, you can invoke pytest with the --cov option. >provide an argument to --cov, specifying which program(s) you want to test. 
> you should indicate the directory into which the report should be written. So in this case, you would say:


### pytest --cov=mymul

> Once you've done this, you'll need to turn the coverage report into something human-readable. I suggest using HTML, although other output formats are available:

### coverage html

> This creates a directory called htmlcov. 
> Open the index.html file in this directory using your browser, and you'll get a web-based report showing (in red) where your program still lacks coverage.
