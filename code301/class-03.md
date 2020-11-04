# Read: 03 - Flexbox and Templating

## Templating with Mustache
Template is HTML markup taht you add template tags to either insert vaiables or run logic.
>  there are no if statements, else clauses, or for loops. Instead, there are only tags
 > It works by expanding tags in a template using values provided in a hash or object.

 ```
> Mustache.render(“Hello, {{name}}”, { name: “Sherlynn” });
// returns: Hello, Sherlynn
```

> Mustache is a specification for a templating language

## A Guide to Flexbox

1.  flexbox is a whole module and not a single property
2. main axis – The main axis of a flex container is the primary axis along which flex items are laid out
3. main-start | main-end – The flex items are placed within the container starting from main-start and going to main-end.
4. main size – A flex item’s width or height
5. cross axis – The axis perpendicular to the main axis
6. cross-start | cross-end – Flex lines are filled with items and placed into the container starting on the cross-start side 
7. cross size – The width or height of a flex item, whichever is in the cross dimension, is the item’s cross size

> I'm seeing so much resource in this page! I am book marking it for reference!

## Flexbox Froggy
> Completed all steps of this tutorial!