# Getting to Know Your CSS Preprocessor
Over the past several years, frontend developers have embraced CSS Preprocessors&mdash;tools that allow you to write and manage your CSS with more functionality. 

CSS Preprocessors address three major issues when writing styles, adding functionality on top of normal CSS functions: How do we better organize our styles (both inside a single file and across multiple files)? How do we handle configuration data and re-used components? How do we ease the pain of repetitive sequences of style definitions?

There are many other doors that open and problems that are solved by trying to solve these three base issues. 

For our project, we are using a CSS Preprocessor called `node-sass`, which allows us to use ["SASS"](http://sass-lang.com) (Syntactically Awesome Style Sheets). SASS, the specification, has been implemented into several different preprocessor tools (such as `node-sass` or the `sass` Ruby Gem). SASS and SCSS (Structured CSS) are terms that tend to be used interchangeably. Technically, SCSS is the piece that adds the hierarchical (nested) capabilities, while SASS is the specification that adds variables and mixin capabilities.

## Variable Definition
Variables are a key piece of creating flexible, consistent systems. Rather than rewriting key information several times across many files, variables allow us to create an information reference we can use everywhere. 

It can be difficult to imagine how useful this will be, but here is an example. One of the most important aspects of any site design is the color palette. In normal CSS, we must define colors as words, hex codes or RGB values. Each time a color is used, we must input the same value. This can be tricky, especially when developers get lazy and use tools to select colors from web pages. Often the tool selects a slightly different shade of the color, so you may see stylesheets that reference several slightly different variations of a color. 

Traditionally, we might see styles like this:

```css
.my-class { color: #aa0000; }
.my-background { background-color: #ab0010; }
.my-success-link { color: green; }
```

If we are using SASS, we can create variables to represent colors:

```sass
$brand-primary: #aa0000;
$brand-success: green;
...
.my-class { color: $brand-primary; }
.my-background { color: $brand-primary;}
.my-success-link { color: $brand-success;}
```

In the SASS example, we could easily change the values of the variables wherever they are defined, and that change would then ripple through all of our styles. So if the `$brand-primary` color changed to "blue" then it would have an immediate and consistent effect on the site styles.

Colors are just one vivid example where having the ability to define variables would be very useful. There are many other situations where defining variables is incredibly useful and helpful for maintaining flexibility and responsiveness in your styles.

## Mixins (Functions)
Another major issue facing frontend developers working on defining styles is repetitive code that needs to be retyped, sometimes with very slight modifiers, over and over again. In most programming, we handle this with "functions". The functions implemented in most CSSS authoring frameworks (like SASS) are called mixins.  

A common use case for using a mixin is when using a feature that is supported by all your target web browsers, but which is still only accessible with a "vendor prefix". (This is often the case when features are nearing finalization, but can sometimes be a situation that can last for years.) If we wanted to get rounded corners on our boxes, mixins allow us to write something like this:

```sass
@mixin border-radius( $radius ){
    -webkit-border-radius: $radius;
    -moz-border-radius: $radius;
    -ms-border-radius: $radius;
    border-radius: $radius;
}

.rounded-box {  @include border-radius( 10px ); }
```

This approach allows us to write one line of code to invoke the mixin, rather than the four lines of style attributes we would need to use. Note that the mixin also accepts a variable (`$radius`), which means we could use this mixin to generate any size of rounded corners.

These three enhancements are powerful enough to have made CSS authoring frameworks a standard part of the frontend development toolkit over the past few years. The future of the CSS standard has no indication that any of these features are going to be rolled into CSS proper in the near-term, so these frameworks and techniques are likely to remain a part of our work.

## Additional SASS/SCSS Learning Resources
This book does not go in-depth on how to use SASS and SCSS to create styles. For the most part, you will apply all of the CSS knowledge that you have to your stylesheets as you normally would. But to learn more about the basic capabilities of SASS and SCSS, and for some insight about how to best leverage these tools to ease your development process.

* [Official SASS Guide](http://sass-lang.com/guide)
* [Getting Started with SASS](http://alistapart.com/article/getting-started-with-sass) by David Demaree
* [The Beginner's Guide to SASS](http://www.webdesignerdepot.com/2013/11/the-beginners-guide-to-sass/) by Andy Leverenz
* [On SASS and Other CSS Preprocessors](https://medium.com/@dannysmith/on-sass-and-other-css-preprocessors-24403fc80b6a) by Danny Smith