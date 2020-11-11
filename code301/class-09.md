# Read: 09 - Refactoring

## Functional Programming Concepts

> “Complexity is anything that makes software hard to understand or to modify." — John Outerhout

Functional programming: 
> programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data — Wikipedia

pure functions:
> definition of purity:
1. It returns the same result if given the same arguments (it is also referred as deterministic)
2. It does not cause any observable side effects

> Reading Files
If our function reads external files, it’s not a pure function — the file’s contents can change.

> Pure functions benefits: The code’s definitely easier to test.

> We combine all these 4 functions and we can "slugify" our string.
1. toLowerCase: converts the string to all lower case
2. trim: removes whitespace from both ends of a strin
3. split and join: replaces all instances of match with replacement in a given string

> Referential transparency

> pure functions + immutable data = referential transparency

> when the expression always remains the same (such as sums)  We can replace the entire expression with a numerical constant and memorize it

> The idea of functions as first-class entities is that functions are also treated as values and used as data.

> Higher-order functions
1. takes one or more functions as arguments, or
2. returns a function as its result

> Filter
The filter function expects a true or false value to determine if the element should or should not be included in the result collection

> Declarative approach
But we want a more declarative way to solve this problem, and using the filter higher order function as well.

> Map
The map method transforms a collection by applying a function to all of its elements and building a new collection from the returned values.

> Reduce
The idea of reduce is to receive a function and a collection, and return a value created by combining the items.

## Refactoring Javascript for Readability

```
// Unrefactored code

const URLstore = [];

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  URLstore.push({[rndName]: URL});
  return rndName;
}

function getLong(shortURL) {
  for (let i = 0; i < URLstore.length; i++) {
    if (URLstore[i].hasOwnProperty(shortURL) !== false) {
      return URLstore[i][shortURL];
    }
  }
}
```

```
// Refactored code

const URLstore = new Map(); // Change this to a Map

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  // Place the short URL into the Map as the key with the long URL as the value
  URLstore.set(rndName, URL);
  return rndName;
}

function getLong(shortURL) {
  // Leave the function early to avoid an unnecessary else statement
  if (URLstore.has(shortURL) === false) {
    throw 'Not in URLstore!';
  }
  return URLstore.get(shortURL); // Get the long URL out of the Map
}
```

```
// Unrefactored code

const friendlyWords = require('friendly-words');

function randomPredicate() {
  const choice = Math.floor(Math.random() * friendlyWords.predicates.length);
  return friendlyWords.predicates[choice];
}

function randomObject() {
  const choice = Math.floor(Math.random() * friendlyWords.objects.length);
  return friendlyWords.objects[choice];
}

async function createUser(email) {
  const user = { email: email };
  user.url = randomPredicate() + randomObject() + randomObject();
  await db.insert(user, 'Users')
  sendWelcomeEmail(user);
}
```

```
// Refactored code

const friendlyWords = require('friendly-words');

const generateURL = user => {
  const pick = arr => arr[Math.floor(Math.random() * arr.length)];
  user.url = `${pick(friendlyWords.predicates)}-${pick(friendlyWords.objects)}` +
    `-${pick(friendlyWords.objects)}`; // This line would've been too long for linters!
};

async function createUser(email) {
  const user = { email: email };
  // The URL-creation algorithm isn't important to this function so let's abstract it away
  generateURL(user);
  await db.insert(user, 'Users')
  sendWelcomeEmail(user);
}
```
> Strategies
Here are some straightforward to implement methods that can lead to easier to read code. There are no absolutes when it comes to clean code — there's always an edge case!

```
Return early from functions:
function showProfile(user) {
  if (user.authenticated === true) {
    // ..
  }
}
```
// Refactor into ->
```
function showProfile(user) {
  // People often inline such checks
  if (user.authenticated === false) { return; }
  // Stay at the function indentation level, plus less brackets
}
Cache variables so functions can be read like sentences:
function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    for (let j = 0; j < continents[i].length; j++) {
      for (let k = 0; k < continents[i][j].tags.length; k++) {
        if (continents[i][j].tags[k] === name) {
          return continents[i][j].id;
        }
      }
    }
  }
}
```
// Refactor into ->
```
function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    const group = continents[i]; // This code becomes self-documenting
    for (let j = 0; j < group.length; j++) {
      const tags = group[j].tags;
      for (let k = 0; k < tags.length; k++) {
        if (tags[k] === name) {
          return group[j].id; // The core of this nasty loop is clearer to read
        }
      }
    }
  }
}
```
Check for Web APIs before implementing your own functionality:
```
function cacheBust(url) {
  return url.includes('?') === true ?
    `${url}&time=${Date.now()}` :
    `${url}?time=${Date.now()}`
}
```

// Refactor into ->
```
function cacheBust(url) {
  // This throws an error on invalid URL which stops undefined behaviour
  const urlObj = new URL(url);
  urlObj.searchParams.append('time', Date.now); // Easier to skim read
  return url.toString();
}
```
