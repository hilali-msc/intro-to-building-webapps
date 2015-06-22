#Background on Our Installation
We will work in what is known as a "Node-based" environment. That is to say, a development environment built on the [Node.js](http://nodejs.org) platform. We will use the ["Yeoman Workflow"](http://yeoman.io) to build our apps, and that will allow us to use several popular tools for frontend development, including [Bower](http://bower.io) and [Grunt](http://gruntjs.com).

We will also use [Git](http://git-scm.org) and [Github](http://github.com) to manage our code and deploy our projects.

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
[Grunt](http://gruntjs.com) is a build manager  and task runner tool. It provides a mechanism for developers to define tasks that can be executed. A task is usually associated with some Node module, and it includes a list of configurations that tell the module how to behave in a given context.

For example, you may use Grunt to configure the `node-sass` module to process all of `.sass` or `.scss` files in your project and put the resulting `.css` files in a specific location. You might then combine that task with several others and roll it all into a command that you can execute by typing `grunt build`.

We will use Grunt in our projects to manage quite a few different tasks. As we work with it, you will come to understand the power of a tool like Grunt. There are many similar tools available for other types of development environment (`rake` in Ruby, `fab` in Python, etc.).

**Please Note**: You will also see another component to the Yeoman Workflow discussed: [Gulp](http://gulpjs.com/). Gulp is an alternative to Grunt that is gaining popularity. Rather than go into details about the differences between Grunt and Gulp, I'll only mention that both are very solid tools and if you wish it is entirely possible to complete this project with either tool. However, for the sake of simplicity, I am focusing on Grunt since it is the default tool that comes connected on most Yeoman generators.

## About Git
Git is a source control software used by many developers for web and many other types of projects. Git is open source and free, which makes it available to everyone. 

Git is also "distributed", which means each person who has a copy possesses the entire history of the project, and each developer could serve as a Git server for any other developer. This allows for a great deal of flexibility when working on projects.

Finally, Git is well-known for the way it handles branching and merging. Although these concepts will only be lightly addressed in the content of this book, these are important features used daily by most developers.

## About Github
Github is a hosting service with enhanced tools to handle code repositories using Git. People are often confused about Git and Github. Think of the way Flickr is a hosting service for your images. Flickr is not a camera or illustration software -- it is a tool that allows people to host their images, organize them into galleries, and connect with others who are doing the same thing. Likewise, Github is a tool that allows you to host your code, work with it using helpful tools (like issue management, or wiki pages for documentation), and then connect with other people who are doing the same thing.

Github offers several services that go far beyond simple "Git repository management", and one of those features is called Github Pages. Github Pages is a static website hosting service, meaning that you can use Github to publish HTML, CSS and Javascript to the web and make it available for the general public.

