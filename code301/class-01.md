# Responsive Web Design and Floats

## Shay Howe’s intro to RWD

The industry came up with an answer to the growing need for mobile compatable apps.  Desktop and mobile users all benefit from responsive web apps. This is called **Responsive Web Design** or **RWD**

**responsive**
> react quickly and positively to any change
**adaptive**
>  easily modified for a new purpose or situation, such as change. 
**mobile**
>  a separate website commonly on a new domain solely for mobile users.

responsive web design favors design that dynamically responds to different browsers and and device views. 

##### Responsive web disgn is broken into 3 parts:
1. flexible layouts: the practice of building the layout of a website with a flexible grid
Flexible grids: relative length units, with percentages or EM
2. Media Queries: extention of media types commonly found when targeting and including styles. 
 it is recommend to use the @media rule inside of an existing style sheet to avoid any additional HTTP requests.

 ```
 <!-- Separate CSS File -->
<link href="styles.css" rel="stylesheet" media="all and (max-width: 1024px)">
```
```
/* @media Rule */
@media all and (max-width: 1024px) {...}

/* @import Rule */
@import url(styles.css) all and (max-width: 1024px) {...}
```
**the and logical operator within a media query allows an extra condition to be added, making sure that a browser or devices does both a, b, c, ect.**

 Viewport: apple invention meta tag to help mobile devices display websites better. 
>  it is recommend that you use the device defaults by applying the device-height and device-width values.
> initial-scale of a website should be set to 1 as this defines the ratio between the device height
> The viewport meta tag will accept individual values as well as multiple values, allowing multiple viewport properties to be set at once.

3. Flexible media: As viewports begin to change size media doesn’t always follow suit. Images, videos, and other media types need to be scalable, changing their size as the size of the viewport changes.
## All About Floats
> Float is a CSS positioning property.
> In web design, page elements with the CSS float property applied to them are just like the images in the print layout where the text flows around them
> There are four valid values for the float property. Left and Right float elements those directions respectively. None (the default) ensures the element will not float and Inherit which will assume the float value from that elements parent element.
> If this parent element contained nothing but floated elements, the height of it would literally collapse to nothing.
Techniques for clearing floats: 
1. the empty div method
2. The overflow method
3. The easy clearing method

## Don’t Overthink It Grids

 “main content area” floated to the left a “sidebar” floated to the right, it’s a simple grid
 > I bookmarked this page for further reference

## CSS Floats Explained By Riding An Escalator

> Floats create alternate flows
Bookmarked for future reference

## SMACSS Official Documentation
> SMACSS (pronounced “smacks”) is more style guide than rigid framework.
> This is an online book giving basic rules for scallable and modular archetecture for CSS. 
> I have bookmarked this as a valuable resource!