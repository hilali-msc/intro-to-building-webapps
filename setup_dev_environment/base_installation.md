#Background on Our Installation
We will work in what is known as a "Node-based" environment. That is to say, a development environment built on the [Node.js](http://nodejs.org) platform. We will use the ["Yeoman Workflow"](http://yeoman.io) to build our apps, and that will allow us to use several popular tools for frontend development, including [Bower](http://bower.io) and [Grunt](http://gruntjs.com).

## About Node.js
Node.js is a development platform that runs Javascript outside of the web browser. This is noteworthy because there are not other major implementations of Javascript outside of the web browser.

The specific Javascript engine Node.js uses is called V8, and it is the engine that is used in Google's Chrome browser. This is a very fast and reliable Javascript engine, and Node is known for being a very fast platform. 

Node allows developers to create tiny Javascript applications called "modules", and then to string those modules together into larger and more complex applications. There are thousands of "Node modules", as they are known. Developers manage modules with a tool called [NPM](https://www.npmjs.com/) (Node Package Manager), which is installed when you install Node.js. 

## About the Yeoman Workflow
[Yeoman](http://yeoman.io) is an application built on the Node.js platform, and it relies on two other programs to make it run: [Bower](http://bower.io) and [Grunt](http://gruntjs.com). All of these are Node.js modules themselves, so they can all be installed with NPM (in one command).

Each part of Yeoman Workflow provides a specific benefit to developers. 