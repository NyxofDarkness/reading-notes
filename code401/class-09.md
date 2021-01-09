# Readings: Game of Greed 4

## Dunder Methods

> Dunder methods let you emulate the behavior of built-in type

> Dunder methods let you emulate the behavior of built-in types. For example, to get the length of a string you can call len('string'). But an empty class definition doesn’t support this behavior out of the box:

``` python
class NoLenSupport:
    pass

>>> obj = NoLenSupport()
>>> len(obj)
TypeError: "object of type 'NoLenSupport' has no len()"
```

> To fix this, you can add a __len__ dunder method to your class:

``` python
class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42
```

> Another example is slicing. You can implement a __getitem__ method which allows you to use Python’s list slicing syntax: obj[start:stop].

> enrich a simple Python class with various dunder methods to unlock the following language features:

[x] Initialization of new objects
[x] Object representation
[x] Enable iteration
[x] Operator overloading (comparison)
[x] Operator overloading (addition)
[x] Method invocation
[x] Context manager support (with statement)

> A constructor in Python is the __init__ dunder:

``` python
class Account:
    """A simple account class"""

    def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []
```

> constructor takes care of setting up the object. In this case it receives the owner name, an optional start amount and defines an internal transactions list to keep track of deposits and withdrawals.

This allows us to create new accounts like this:

``` python
>>> acc = Account('bob')  # default amount = 0
>>> acc = Account('bob', 10)

```

> Iteration: __len__, __getitem__, __reversed__

> It’s common practice in Python to provide a string representation of your object for the consumer of your class (a bit like API documentation.) There are two ways to do this using dunder methods:

1. __repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.

2. __str__: The “informal” or nicely printable string representation of an object. This is for the enduser.

> Operator Overloading for Comparing Accounts: __eq__, __lt__
> Operator Overloading for Merging Accounts: __add__
> Callable Python Objects: __call__
> Context Manager Support and the With Statement: __enter__, __exit__

## Statistics - Probability

> At the most basic level, probability seeks to answer the question, “What is the chance of an event happening?”

> a probablity example of flipping a coin:

``` python
import random
def coin_trial():
heads = 0
for i in range(100):
    if random.random() <= 0.5:
        heads +=1
    return heads
def simulate(n):
    trials = []
    for i in range(n):
        trials.append(coin_trial())
    return(sum(trials)/n)
simulate(10)
>>> 5.4
simulate(100)
>>> 4.83
simulate(1000)
>>> 5.055
simulate(1000000)
>>> 4.999781
```

Videos

## Intro to Statistics

> The most important qualities to notice about the normal distribution is its symmetry and its shape.

> ability to give graphic meaning to data thus making it easier to explore the data and give close to accurate decisions

## AI Guru makes $238,800 with misleading paid course. doesn’t credit developers

> Point 1 - Why you should anyways fork: Forking on GitHub displays the repository as a forked repository and keeps the commit history, effectively crediting the original author. It also shows the differences in commits and code so it's publicly visible what you contributed and what's from the original author. The other reason is a lot of code has attribution in its license (e.g. GPL License V3). Thus it's illegal to simply copy it without due credit. 

Point 2 - The 'Merge' thing: what you're describing is actually a git diff, not a merge. It shows the changes in code, what's added and deleted. The diff is used when you want to merge say 2 different people's code, so you can see who changed what. 
-Hengjian Jia

Big Takaway: ATTRIBUTION ALWAYS!

Bookmark/Skim
[x] done! Statistics Module