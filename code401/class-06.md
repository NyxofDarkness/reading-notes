# Readings: Game of Greed 1

## How to use Random Module

>Why to use this: We want the computer to pick a random number in a given range Pick a random element from a list, pick a random card from a deck, flip a coin etc

> Randint accepts two parameters: a lowest and a highest number: this is to get a random integer

```python

import random
print random.randint(0, 5)

```

> If you want a larger number, you can multiply it.

```python

import random
random.random() * 100

```

> enerate a random value from the sequence sequence.

```python

random.choice( ['red', 'black', 'green'] ).
```

> The choice function can often be used for choosing a random element from a list.

```python

import random
myList = [2, 109, False, 10, "Lorem", 482, "Ipsum"]
random.choice(myList)

```

> The shuffle function, shuffles the elements in list in place, so they are in a random order.

```python

from random import shuffle
x = [[i] for i in range(10)]
shuffle(x)
Output:
# print x  gives  [[9], [2], [7], [0], [4], [5], [3], [1], [8], [6]]
# of course your results will vary

```

> Generate a randomly selected element from range(start, stop, step)

```python

random.randrange(start, stop[, step])
import random
for i in range(3):
    print random.randrange(0, 101, 5)

```

## What is Risk Analysis

> In any software, using risk analysis at the beginning of a project highlights the potential problem areas.

possible risks you could encounter:

1. Use of new hardware
2. Use of new technology
3. Use of new automation tool
4. The sequence of code
5. Availability of test resources for the application

> risk magnitude indicators:

1. High: means the effect of the risk would be very high and non-tolerable. The company might face loss.

2. Medium: it is tolerable but not desirable. The company may suffer financially but there is a limited risk.

3. Low: it is tolerable. There lies little or no external exposure or no financial loss.

> risk identification

1. Business Risks: This risk is the most common risk associated with our topic. It is the risk that may come from your company or your customer, not from your project.

2. Testing Risks: You should be well acquainted with the platform you are working on, along with the software testing tools being used.

3. Premature Release Risk: a fair amount of knowledge to analyze the risk associated with releasing unsatisfactory or untested software is required

4. Software Risks: You should be well versed with the risks associated with the software development process.

> 3 perspectives of risk manegment:

1. Effect – To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.

2. Cause – To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.

3. Likelihood – To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied

> How to perform Risk Analysis?
> There are three steps:

1. Searching the risk

2. Analyzing the impact of each individual risk

3. Measures for the risk identified

## Video Big O Notation

Quote from Christine Hill 
> Here's my favorite Big O analogy:
Let's say you're making dinner for your family. O is the process of following a recipe, and n is the number of times you follow a recipe.
O - you make one dish that everyone eats whether they like it or not. You follow one recipe from top to bottom, then serve (1 recipe). <-- How I grew up
O(n) - you make individual dishes for each person. You follow a recipe from top to bottom for each person in your family (recipe times the number of people in your family).
O(n^2) - you make individual dishes redundantly for every person. You follow all recipes for each person in your family (recipe times the number of people squared).
O(log n) - you break people into groups according to what they want and make larger portions. You make one dish for each group (recipe times request)



## skimmed and Bookmarked: Python Random

## What is Dependency Injection