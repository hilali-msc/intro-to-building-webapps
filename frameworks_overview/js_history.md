# A Brief History of Javascript in Web Development
The web is a strange place. We use all sorts of technologies to create websites that do all sorts of things. We use Java and Ruby and Python and PHP and myriad other language; we use nginx and Apache and Tornado and Twisted and all sorts of servers made for specific purposes; we use mySQL and Posgresql and MongoDB and Cassandra to store data for use in dynamic applications. This list just barely hints at the surface of how diverse and complex the server-side components of any given web application can be.

On the client-side, things are quite a bit different.

Web browsers are built to adhere to standards. Most of the core standards and specifications governing the Web are created by the World Wide Web Consortium (W3C). The W3C publishes standards that, for example, govern how Hypertext Markup Language (HTML) should be interpreted, how Cascading Stylesheets (CSS) work, and what APIs are revealed on the Document Object Model (DOM). These standards then dictate what browsers do when they receive HTML, CSS and Javascript from the server.

And that's a key point: The browser itself only understands HTML, CSS and Javascript. Functionality can be expanded using plugins and extensions, but those are browser-specific and proprietary. At the fundamental level, all websites boil down to the HTML, CSS and Javascript.

HTML is the core building block of any given webpage. The HTML provides a structure that defines the content on the page so the browser "knows" what exists in that page. CSS is a means of configuring the visual presentation of HTML elements. HTML structure allows CSS to reference content on the page using element names, classes, or IDs, tying the HTML and CSS together directly.

Javascript interacts with the page using the DOM, which is a programmatic representation of the structure of the HTML. The browser downloads the HTML, reads it, interprets it, and then holds the dynamic, programmatic representation of that HTML, the DOM, in memory while the page is being viewed.

Of the three primary web technologies that make a page live and breathe in your browser, Javascript is the only one that is a programming language. HTML is a markup language: it describes content using HTML elements. CSS is a configuration language: it defines settings for visual presentation of HTML elements. Javascript is a programming language: it allows you to create logical definitions and structures that can provide dynamic response to user actions.

Because Javascript is the only programming language that is interpreted and executed in the web browser, it enjoys a special place in the world of web development. This is why Javascript is so important.

## Early Javascript
Javascript was created by Brendan Eich at Netscape and was introduced in 1995 through the Netscape browser. Microsoft adopted Javascript in 1996 with Internet Explorer 3, and since then Javascript has been a part of the web. 

In 1997 Ecma International, a standards organization based in Europe, released the first ECMAScript standard, lending Javascript governance outside of a single company. ECMAScript standards have been released steadily ever since, with the latest being ECMAScript v. 6, which released in June 2015.

At first, Javascript was used for very basic features, many of which have since become absorbed into other technologies. For example, at one point it was common to use Javascript to handle "image rollovers"&mdash;making images switch when the user moved the mouse cursor over them. Using this technique brought about a revolution in web design with sites that had more graphic navigation bars that could highlight current and active menu options.

Javascript had the ability to modify elements in the DOM, but the native APIs for working with the DOM were clunky and limited. In the early 2000s Javascript developers created libraries, which grew into frameworks, to make manipulating the DOM much easier. Numerous libraries competed, including MooTools, Dojo, and ExtJS, but the library that became a framework that ruled Javascript development for many years was jQuery.

jQuery introduced the `$()` (often pronounced "dollar sign query"), which was a shorthand way of referencing the main `jquery` object. The "query" part of jQuery came from the fact that developers could use CSS notation to select DOM elements, allowing them to "query" the DOM for the elements they want.

With jQuery, one may write:

```js
$('nav a').on("click", function(el){ 
    el.addClass('demo');
});
```

That code would add a "click" listener to all of the links that are inside the `<nav>` element. To do the same thing with native APIs would take many more lines of complex code.

jQuery has been a great solution for making dynamic web pages in many ways: 

* It provides a great set of tools for developers.
* It generally plays nicely with unrelated Javascript, so you can use it alongside lots of other tools.
* It has good support for making "AJAX" (asynchronous Javascript) requests.
* It has a "plugin" system that allows developers to create custom functionality and complex modules to make specific effects happen, and those plugins can be leveraged in a fairly standardized way.

## Recent Javascript
Recently, Javascript has enjoyed another surge of popularity. Already firmly established since the creation of frameworks like jQuery, Javascript has moved everywhere the web has moved. As televisions, in-car navigation systems, and mobile devices have all leveraged web technologies, Javascript has become a part of those ecosystems.

In 2009 Node.js was created, giving developers a very fast and robust implementation of a Javascript engine that could run on the server. This has opened the door to a whole new wave of module development, with thousands of modules now created for Node.js. The architectural concepts pushed by Node.js have led to changes in how webapps and websites use interdependent Javascript modules. 

The rise of Node.js popularity has led to Javascript being placed on all sorts of embedded machines, too. There is a whole subculture built around gadgets, like drones and hobby robots, powered by Javascript code. 

The enhanced interest in using Javascript has led to other noteworthy developments, too. The entire development environment and stack that we are using for this project is Javascript-based. As we build our pages we use a huge array of Javascript tools to help us, and we write Javascript that runs in the browser for our users as they use our sites. 

Javascript, again, is everywhere.


