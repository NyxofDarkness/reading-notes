# Reading 34

## Dunder Methods

> dunder methods are a set of predefined methods you can use to enrich your classes

> Dunder methods let you emulate the behavior of built-in types. For example, to get the length of a string you can call len('string'). But an empty class definition doesn’t support this behavior out of the box:

``` python
# this
class NoLenSupport:
    pass

>>> obj = NoLenSupport()
>>> len(obj)
TypeError: "object of type 'NoLenSupport' has no len()"

# becomes this:
class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42
```

> Use dunder methods to unlock the following features:

-Initialization of new objects
-Object representation
-Enable iteration
-Operator overloading (comparison)
-Operator overloading (addition)
-Method invocation
-Context manager support (with statement)

> a constructor in Python is the __init__ dunder:

> If you don’t want to hardcode "Account" as the name for the class you can also use self.__class__.__name__ to access it programmatically.

> __repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.

> __str__: The “informal” or nicely printable string representation of an object. This is for the enduser.

## Iterators

> Objects that support the __iter__ and __next__ dunder methods automatically work with for-in loops.

> Because there’s never more than one element “in flight”, this approach is highly memory-efficient. Our Repeater class provides an infinite sequence of elements and we can iterate over it just fine.

> First setting up and retrieving the iterator object with an iter() call, and then repeatedly fetching values from it via next().

> Python iterators normally can’t be “reset”—once they’re exhausted they’re supposed to raise StopIteration every time next() is called on them. To iterate anew you’ll need to request a fresh iterator object with the iter() function.

> Iterators provide a sequence interface to Python objects that’s memory efficient and considered Pythonic. Behold the beauty of the for-in loop!
To support iteration an object needs to implement the iterator protocol by providing the __iter__ and __next__ dunder methods.
Class-based iterators are only one way to write iterable objects in Python. Also consider generators and generator expressions.

## Generators

> This is what the class looked like in its second (simplified) version:

``` python
# This repeater example seems comp[licated
class Repeater:
    def __init__(self, value):
        self.value = value

    def __iter__(self):
        return self

    def __next__(self):
        return self.value

# but with a generator, it's easy!
def repeater(value):
    while True:
        yield value
```

> Whereas a return statement disposes of a function’s local state, a yield statement suspends the function and retains its local state.
