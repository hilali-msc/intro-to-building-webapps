#Background on Our Installation
We will work in what is known as a "Node-based" environment. That is to say, a development environment built on the [Node.js](http://nodejs.org) platform. We will use the ["Yeoman Workflow"](http://yeoman.io) to build our apps, and that will allow us to use several popular tools for frontend development, including [Bower](http://bower.io) and [Grunt](http://gruntjs.com).

## About Node.js
Node.js is a development platform that runs Javascript outside of the web browser. This is noteworthy because there are not other major implementations of Javascript outside of the web browser.

The specific Javascript engine Node.js uses is called V8, and it is the engine that is used in Google's Chrome browser. This is a very fast and reliable Javascript engine, and Node is known for being a very fast platform. 

Node allows developers to create tiny Javascript applications called "modules", and then to string those modules together into larger and more complex applications. There are thousands of "Node modules", as they are known. Developers manage modules with a tool called [NPM](https://www.npmjs.com/) (Node Package Manager), which is installed when you install Node.js. 

## About the Yeoman Workflow
[Yeoman](http://yeoman.io) is an application built on the Node.js platform, and it relies on two other programs to make it run: [Bower](http://bower.io) and [Grunt](http://gruntjs.com). All of these are Node.js modules themselves, so they can all be installed with NPM (in one command).

Each part of Yeoman Workflow provides a specific benefit to developers. 

### Yeoman
[Yeoman](http://yeoman.io) is a templating tool. It provides a method for developers to create project templates, which are useful because they allow us to get "project skeletons" up and running very quickly. This process is often known as "bootstrapping" a site: bringing it up from nothing.

A project skeleton is a basic project structure that works, but without any customized features or functions. These are typically based on best practices approaches, and they involve the interlinking of several components.

In the world of Javascript there are many options for each component. With the Yeoman Workflow you are free to use any combination of components you wish, but you are also empowered with the ability to quickly create project skeletons that define the basic structure of a project.

This is useful in two ways: First, once you find a project template (or "generator" in the Yeoman lingo) that works for your development needs, you can easily re-use that template to start new projects. This allows you to get more quickly to the task of building new webapps. 

Second, this is a useful learning tool because you can quickly bring up projects based on technology that you may not yet have mastered (like now). Although you have not made all the choices to put these components together, you are able to learn from the developers who have come before you. Once you learn your way around this blend of components, it will be easier to move on to new approaches and tools.

### Bower

[Bower](http://bower.io) is a package management tool, somewhat like NPM. It allows developers to define a "manifest" of frontend components a website makes use of. This might be jQuery or Bootstrap, or it could be AngularJS components and additions to support mobile hybrid apps. There are, as with NPM, many frontend development tools and libraries that support management with Bower.

This package manager allows you to more easily add and remove components from your website as you work through your development and maintenance. You can specify each version of the components you require, allowing you to maintain your site independent of when libraries or frameworks update themselves.

### Grunt