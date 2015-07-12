# Web Application Frameworks: An Overview
This section covers the broad topic of "web application frameworks", and aims to give you a broader understanding of why we are doing things the way we are. This topic is really still too broad for a single section, so we will cover many of the foundational concepts somewhat lightly. The hope is that given a general understanding and then some practical experience working within a framework, you will then be able to go out and engage more effectively with the many other great learning resources already available for various specific frameworks and approaches.

## What is a "framework"?
Framework is a term used to address a collection of pre-created code that can be used to augment an application designed for the end user. Frameworks are designed for developers, and they aim to "take care" of the repetitive (or "boilerplate") code that we often must generate to get a project up and running. 

Take, for example, [the Django framework](http://djangoproject.com). Django is a framework written in Python, which means that if you are using it, then you should be writing your application in Python. Django is a framework designed to create websites. It contains code that can speed your development by giving you systems for handling HTTP requests, routing URLs, processing templates, accessing databases, and much more. If you wish to make a new page, or connect to your database, there are pieces in Django that make that process much easier.

However, Django, itself, is not an application. It's not like [Wordpress](http://wordpress.org), for example, which is a content management system. When you "install" Django, you are really just adding it to a project (just like we have added Javascript modules to our webapp project already). In order to have anything you could use to, say, post a blog online, you would need to write additional Python code to define your site and the content you wish to make available. 

When you install Wordpress, you have a functional blog site that you can then modify into any number of types of content-based website. 

This is a major difference between an application and a framework: All by themselves, frameworks are nothing but a box of parts waiting to be assembled into a functioning application.

Frameworks often also dictate what we build. For example, if your goal were to build an in-browser game, Django would likely not be helpful for easing the development of the player's interactions or your game screen display. Frameworks for handling games and animation have very different pieces in the box than frameworks designed for handling HTTP requests and database connections.

Frameworks are also often used in conjunction. In the example described above, you may use a framework like Django to run the data and HTTP server portion of your game (so you can store user profiles, high score tables, etc.) and then you could use a framework like [Crafty.js](http://craftyjs.com/) for actually making the game run. 

## Why do I need one?
There was a time when no websites used frameworks. In the beginning there was the "static website":  that is, sites where all the files are uploaded and as you navigate the site you move between real files present on the server's storage drives. 

Quickly, nascent web developers created what would ultimately come to be known as "static website generators", which were scripts that would process templates written in various formats to build stacks of real files on the server's storage drives. (It's worth nothing that this approach has remained with us today, and has enjoyed a renaissance as storage costs have plummeted and cheap or free static website hosting has become plentiful.)

Developers also quickly moved into creating web-oriented frameworks across many favorite languages. We saw the fast rise of things like ASP.NET and JavaEE Servlets. These large technologies dominated for the first decade of the Web, and served the primitive web well. But it was quickly realized that we needed a better way to handle the growing complexity of building websites. 

In the mid-2000s there was another boom in web application framework design. Microsoft dropped the "ASP" and released .Net, a greatly improved framework that uses C# as the programming language. Java continued to ride high as a language with the release of several popular frameworks including Struts, Web Objects, and Google Web Toolkit. Even Perl, which was the language of the "CGI-BIN", got into the act with frameworks like Catalyst gaining popularity around the time.

In addition to the "enterprise" level of web application frameworks on offer from major players working with well-supported languages, several serious competitors came out that have ultimately had a major effect on the web world. PHP took off in the mid-2000s, opening the door to low-cost dynamic backend web development for many more potential developers and websites. PHP frameworks like CakePHP, Symfony, and Zend remain popular today.

As PHP boomed, so did other languages online. Python and Ruby both saw a serious increase in popularity beginning around 2005 that continues today. In the Python world early frameworks like ZOPE, web2py, and Pylons laid the groundwork for getting Python onto web servers. The Django framework has continued to dominate Python-based web development.

Ruby's most popular web application framework is Rails, popularized by a group of bombastic creators and enthusiastic supporters. Rails was the first popular framework to boast robust database integration so that developers did not have to hand code SQL in order to make their apps run. This made Rails immensely friendly to developers who wish to rapidly create content types and use them in innovative ways.

The approaches pioneered in the mid-2000s have continued to grow and evolve. Although Django and Rails are both dominant frameworks today, there are numerous alternative frameworks (such as Flask and Sinatra) that aim to serve various types of websites within various types of contexts. 

Although the BEST way to build a webapp is far from settled, one thing we appear to have learned over the years is that if you're going to build webapps, you will likely benefit from using a framework.

## What about Javascript?
You may have noticed that all of the discussion so far has focused on backend languages. That's because the story of Javascript frameworks is both shorter and longer than the summary given above. Although serious usage of Javascript frameworks has not been at the foreground of web development for as long, over the past five years Javascript has become an even more important component of building websites. 

Javascript is everywhere, and developers are using it in amazing new ways every day. 
