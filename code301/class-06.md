# reading: 06

## An Introduction to Node.js on sitepoint.com

Two definitions for Node.js include: 

> Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.

> Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.

Node.js is built in the open-source javascript engine that runs google chrome and other chromium-based web browsers, the V8 engine. 

>  the creator of Node (Ryan Dahl) took the V8 engine and enhanced it with various features, such as a file system API, an HTTP library, and a number of operating system–related utility methods

> npm is a package manager that come bundled with Node

```
npm -v
```
shows you what version you have 

```
npm install -g jshint
```
installs the jshint package locally on your system

> You should now see a number of ES6-related errors. If you want to fix them up, add /* jshint esversion: 6 */

```
npm init -y
```
> This will create and auto-populate a package.json file in the same folder.

```
npm install lodash --save
```
> use npm to install the lodash package and save it as a project dependency:

> And if you want to start developing apps with any modern JavaScript framework (for example, React or Angular), you’ll be expected to have a working knowledge of Node and npm (or maybe Yarn).

instructiong for the Node:

> We start by requiring Node’s native HTTP module. We then use its createServer method to create a new web server object, to which we pass an anonymous function. This function will be invoked for every new connection that’s made to the server.

> The anonymous function is called with two arguments (request and response). These contain the request from the user and the response, which we use to send back a 200 HTTP status code, along with our “Hello World!” message.

> Finally, we tell the server to listen for incoming requests on port 3000, and output a message to the terminal to let us know it’s running

Uses for node: 
> For example it can be used as a scripting language to automate repetitive or error prone tasks on your PC. It can also be used to write your own command line tool, such as this Yeoman-Style generator to scaffold out new projects.

> Node.js can also can be used to build cross-platform desktop apps and even to create your own robots.> 