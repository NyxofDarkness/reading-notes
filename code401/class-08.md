# Readings: Game of Greed 3

## List Comprehensions

> List comprehensions provide a concise way to create lists.

1. it has brackets containing an expression followed by a for clause, then
zero or more for or if clauses.

2. The expressions can be anything, meaning you can
put in all kinds of objects in lists -> result will be a new list resulting from evaluating the expression in the
context of the for and if clauses which follow it.

>  list comprehension always returns a result list.

``` python
new_list = [expression(i) for i in old_list if filter(i)]
```
> The list comprehension starts with a ‘[‘ and ‘]’, square brackets, to help you remember that the
result is going to be a list.

> The basic syntax uses square brackets.

``` python
[ expression for item in list if conditional ]
```

* new_list

The new list (result)

* expression(i)

Expression is based on the variable used for each element in the old list

* for i in old_list

The word for followed by the variable name to use, followed by the word in the
old list

* if filter(i)

Apply a filter with an If-statement

> start easy by creating a simple list.

``` python
x = [i for i in range(10)]
print x

# This will give the output:
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

> list with squares!

``` python
# You can either use loops:
squares = []

for x in range(10):
    squares.append(x**2)
 
print squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Or you can use list comprehensions to get the same result:
squares = [x**2 for x in range(10)]

print squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

> multiply each item in list by 3 and return a new list:

``` python
list1 = [3,4,5]
 
multiplied = [item*3 for item in list1] 
 
print multiplied 
[9,12,15]
```

> We will take the first letter of each word and make a list out of it.

``` python
listOfWords = ["this","is","a","list","of","words"]

items = [ word[0] for word in listOfWords ]

print items
The output should be: [‘t’, ‘i’, ‘a’, ‘l’, ‘o’, ‘w’]
```

> you can convert lower case / upper case letters.

``` python
>>> [x.lower() for x in ["A","B","C"]]
['a', 'b', 'c']

>>> [x.upper() for x in ["a","b","c"]]
['A', 'B', 'C']
```

> This example show how to extract all the numbers from a string.

```python
string = "Hello 12345 World"
numbers = [x for x in string if x.isdigit()]
print numbers

>> ['1', '2', '3', '4', '5']
Change x.isdigit() to x.isalpha() if you don’t want any numbers.
```

> Create a text file and put in some text in it.

this is line1
this is line2
this is line3
this is line4
this is line5

Save the file as test.txt

##### Then create the filter by using list comprehension:

``` python
fh = open("test.txt", "r")

result = [i for i in fh if "line3" in i]

print result
```

Bookmark/Skim
[x] done! Primer on Decorators
