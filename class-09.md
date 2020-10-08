# Read:09

From the Duckett HTML book:

## Chapter 7: “Forms” (p.144-175)

>Whenever you need to collent information from visitors you will use a form which lives inside the < form > element

**form information** sent in name/value pairs

> each control is given a name and the text the user types in or the values of the objects that select are sent to the server

> HTML% has new form elements that amke it easier for visitors to fill in forms
1. form validation
2. date input
3. email and url input
4. search input
example forms on 171-172

## Chapter 14: “Lists, Tables & Forms” (pp.330-357)

The .on() method has two additional properties that let you: filter the initial jquery to respond tyo subset elements, and pass extra information into the event handler using object literal notation

* delegating events
* effects, transistions and movement
* basic effects
* animating CSS properties- .animate() allows you to create some of your own effect and animations by changing css properties
* using animations- page 335. **TRY THIS OUT!**
* traversing the DOM-When you have amde a jquery selection you can use these methods to access other element nodes relative to the initial selection
* traversing- pg. 337
* add and filter elements in a selection
* filters in use-examples select all list items and uses different filters to select a subset of the items in the list to work with
* finding items by order
* using index numbers
* selecting from elements
* form methods and events
* working with forms
* cutting and copying elements
* cut, copy, paste
* box dimensions
* changing dimensions
*window and page dimensions
* position of elements on the page **very impotant**
* determining positions of items on page
in addition to hosting the jquery file with the rest of your website, you can use a version that is hosted by other companies, however you should include a fallback version just in case something happens to them.
* You can load a jquery from a CDN
* protocol relative URL= url for the script starts with two forward slashes
The position of the script elements can affect how quickly the page loads. 
* If the script tries to access an element before it has loaded, it causes an error



From the Duckett JS book:

## Chapter 6: “Events” (pp.243-292)

* events are the browsers way of telling you something has happened
* like when the page is finished loading or a button has been clicked
* binding is the process of stating which event you are waiting to happen, and which element you are waiting for that event to happen
* when an event occors on an element: triggers a javascript functiuon
* it feels interactive because that function changes the webpage in some way
* you can use event delegation to monito for events.
* all teh children of an element can experience this
* W3C DOM events are commonly used, although there are others in HTML5 and browser specific events