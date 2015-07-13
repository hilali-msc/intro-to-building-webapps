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

## The challenge of progressive enhancement
The generation of Javascript libraries that birthed tools like jQuery in the mid-2000s was an era built around "progressive enhancement" (and, sometimes, progressive enhancement's less appealing cousin, "graceful degradation"). Developers could not be sure that all users would have browsers supporting Javascript, and if they did standards adoption among browser makers could be spotty, so the Javascript might not work. Because of this, developers had to always guard against breakage.

To help with this, tools like jQuery were made to enhance the vanilla HTML and CSS that would normally be delivered to the page. Properly done, pages could be created that were totally usable in a traditional, "click and refresh", way if the Javascript failed to load. But if the Javascript succeeded at loading, then pages would come alive with background updates, fancy interfaces, and more.

This approach is still worthwhile, and for many purposes it may still be a great idea to think about a project from a progressive enhancement point of view. For example, if you are building a site that is dedicated to showing off specific content, or providing access to media files, there is a lot that can be conveyed in traditional HTML. That content can be loaded and accessible to a wide range of devices, then Javascript, which is very reliable these days, can enhance the content to provide modern features.

But there are limitations to progressive enhancement. For example, what if you have a web application, and this application relies on the interaction of the user with Javascript to have any value? We aren't imaginging a site that wants to show you a video; imagine instead a site that wants to help you make a video. What is the value of a "static" or "traditional" page in that context? Probably not much.

## What webapps want
Dynamic webapps have a whole different set of considerations. If Javascript is not enabled, then the entire app is going to be unusable. So why bother having robust fallback content? (Other than a helpful error message, of course.)

Other issues come up when you build webapps:

* With jQuery, we could make a quick call to see if, for example, piece of content was favorited, or to send a new favorite to the server in the background. But what if we want to build an app where all of the screens have access to the data for objects in the system, and where we keep all that data synchronized across multiple views? This becomes very complex using only jQuery or similar solutions. We need a better way of **managing and modeling data** for use in our app.
* With progressive enhancement, we could enhance pages by making tab layouts or other custom effects. But what if we want to provide consistent headers and footers? What about slide-out menus that are the same across multiple views? These are the sorts of interface elements that exist in applications, but not so much in content-based websites. We need a better way to handle **templating views** so we can better manage our interface.
* Since we do not want to make a page request to the server on each click, we cannot rely on standard links to be interpreted by a web server to move our users around our webapp. This provides us with a challenge of knowing which views to show our users as they move through our application. We require a **routes mechanism** that can be used to define specific "locations" inside our webapp.

These are just a few of the major challenges we face when we try to build more app-like websites, and the old methods just don't work.

Fortunately, developers are never short of "new methods", and we are amid a boon of what are commonly known as "Single Page Application Frameworks". Webapps (also often known as "Single Page Applications (SPAs)") are the way developers are thinking these days, and developers have many different approaches to solving all of these challenges.
