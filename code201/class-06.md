# Read: 06 - JS Object literals; The DOM

## Chapter 3: “Object Literals” (pp.100-105)

> What is an Object?

1. objects group together a set of variables and functions to create a model of something you would reconize from the real world
2. in an object vaiables become known as properties
3. in an object functions become known as methods

*like variables and named functions, objects have names too. 
*They must be unique so they can be called upon. 
> An objects name is called a key

> kinds of object writing:
1. literal notations
* checkavailability()
* hotel.checkavailability()

2. and dot notations!
* checkavailability()
* byou can have two objects on same page, use the same notation, but store them in variables with different names


## Chapter 5: “Document Object Model” (pp.183-242)

1. The browser uses the DOM tree to represent the page
2. DOM trees 4 types of nodes. **document nodes**, **element nodes**, **attribute nodes**, **text nodes**
3. you can select nodes using: **id or class attributes**, **tag name**, **CSS selecter Syntax**
4. If a DOM query tries to return more than one node, it comes as a **nodelist**
5. access and update content using **textcontent**, **innerHTML**
6. element nodes can contain multiple text nodes and child elemtns that are siblings of each other
7. jquery is popular because older browsers are inconsistant in using DOM
8. Browsers have tools to see DOM, **inspect**