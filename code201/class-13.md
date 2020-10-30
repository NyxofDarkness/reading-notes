## “The Past, Present, and Future of Local Storage for Web Applications”

* Cookies were invented early in the web’s history, and they can be used for persistent local storage of small amounts of data. 

**Here are the potentialy dealbreaking downsides:**

1. Cookies are included with every HTTP request: slows down the browser and application
2. Cookies are included with every HTTP request: not secure way of sending data, it's exposed
3. Cookies are limited to about 4 KB of data: not enough to be useful

**What we really want is**

1. more storage space
2. on the client that persists beyond a page refresh and isn’t transmitted to the server
3. “HTML5 Storage” is a specification named Web Storage
4. HTML5 Storage it’s a way for web pages to store named key/value pairs locally, within the client web browser. **this data persists even after you navigate away from the web site, close your browser tab, exit your browser, or what have you. Unlike cookies, this data is never transmitted to the remote web server (unless you go out of your way to send it manually)**


> How to check for html5 storage:
`function supports_html5_storage() {`
 ` try {`
   ` return 'localStorage' in window && window['localStorage'] !== null;`
  `} catch (e) {`
    `return false;`
 ` }`
`}`

> you can use Modernizr to detect support for HTML5 Storage

`if (Modernizr.localstorage) {`
 ` // window.localStorage is available!`
`} else {`
  `// no native support for HTML5 storage :(`
  `// maybe try dojox.storage or a third-party solution`
`}`

> Like other JavaScript objects, you can treat the localStorage object as an associative array. Instead of using the getItem() and setItem() methods, you > can simply use square brackets. For example, this snippet of code:

`var foo = localStorage.getItem("bar");`
`// ...`
`localStorage.setItem("bar", foo);`
`…could be rewritten to use square bracket syntax instead:`

`var foo = localStorage["bar"];`
`// ...`
`localStorage["bar"] = foo;`

> removing the value for a given named key, and clearing the entire storage area

`interface Storage {`
  `deleter void removeItem(in DOMString key);`
  `void clear();`
`};`

> property to get the total number of values in the storage area

`interface Storage {`
 ` readonly attribute unsigned long length;`
  `getter DOMString key(in unsigned long index);`
`};`

> Every time a change occurs within the game, we call this function:

`function saveGameState() {`
   ` if (!supportsLocalStorage()) { return false; }`
    `localStorage["halma.game.in.progress"] = gGameInProgress;`
   ` for (var i = 0; i < kNumPieces; i++) {`
`	localStorage["halma.piece." + i + ".row"] = gPieces[i].row;`
`	localStorage["halma.piece." + i + ".column"] = gPieces[i].column;`
  `  }
 `   localStorage["halma.selectedpiece"] = gSelectedPieceIndex;`
 `   localStorage["halma.selectedpiecehasmoved"] = gSelectedPieceHasMoved;`
 `   localStorage["halma.movecount"] = gMoveCount;`
 `   return true;`
`}`

