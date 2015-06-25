# Getting to Know Your CSS Preprocessor
Over the past several years, frontend developers have embraced CSS Preprocessors&mdash;tools that allow you to write and manage your CSS with more functionality. 

CSS Preprocessors address three major issues when writing styles, adding functionality on top of normal CSS functions: How do we better organize our styles (both inside a single file and across multiple files)? How do we handle configuration data and re-used components? How do we ease the pain of repetitive sequences of style definitions?

There are many other doors that open and problems that are solved by trying to solve these three base issues. 

For our project, we are using a CSS Preprocessor called `node-sass`, which allows us to use ["SASS"](http://sass-lang.com) (Syntactically Awesome Style Sheets). SASS, the specification, has been implemented into several different preprocessor tools (such as `node-sass` or the `sass` Ruby Gem). SASS and SCSS (Structured CSS) are terms that tend to be used interchangeably. Technically, SCSS is the piece that adds the hierarchical (nested) capabilities, while SASS is the specification that adds variables and mixin capabilities.

## Style Organization and Hierarchy (Nesting)
Stylesheets are tricky to manage. This is primarily a result of the flexibility we have with implementing CSS and the "cascading" priority of styles. In order to determine which style applies to an element when there are multiple styles that target that element, CSS implements a notion of "specificity". The concept of specificity and the intricacies of how it works are well described in Andy Clarke's classic essay, ["CSS Specificity Wars"](http://www.stuffandnonsense.co.uk/archives/css_specificity_wars.html). 

The trickiness with specificity is that it can be tough when you are in a huge file to keep track of all the style definitions. The fact that many stylesheets on large projects become files with thousands of lines of style definitions adds to the problem.

Stylesheets tend to grow to huge sizes because developers want to precisely control how styles go together. If developers break styles into multiple files, and then link stylesheets to the webpage in the traditional manner (with a `<link>` tag), then other issues can crop up in terms of page speed and style linking order (which, of course, can cause major issues with styles rendering correctly.)

CSS Preprocessors help with these issues in two ways. First, when you are writing styles inside a stylesheet, you can use "SCSS" hierarchies (also known as "nesting"). (**Please Note:** SCSS is a *superset* of CSS, so you can always just write "normal" CSS and that will work.)

Here is an example to show how normal CSS might compare to the SCSS version. First, the plain CSS example:

```css
.my-container a:link,
.my-container a:active,
.my-container a:visited {
    color: red;
}
.my-container a:hover {
    color: green;
}
```

The equivalent SCSS code to the example above looks like this:

```sass
.my-container {
    a {
        &:link, &:active, &:visited {
            color: red;
        }
        &:hover {
            color: green;
        }
    }
}
```

As you work with hierarchical definitions of styles, you should also keep in mind the "3-levels Rule". This is a rule of thumb that you should avoid having your styles go more than 3 levels deep in hierarchy. This will help you in two ways: First, you will have more easily readable stylesheets; second, the styles that are produced by the preprocessor will not be as efficient as shorter styles. Remember that writing styles is always a balance of being specific enough and not over-specifying. 

It's also easy to see how styles can be better organized within a file because we can use larger element styles (`.my-container` in the example above) to contain styles affecting the child elements.

The other way in which preprocessors help you with hierarchy and organization is via the `@import` command.

Imagine that you have a large web project and you have a stylesheet that has possibly thousands of lines of style definitions. If you look at those styles, you could probably group them according to what function they perform in your project (menus, buttons, content styles, etc.). Using your preprocessor, you can now break up those giant files into much smaller files.

Imagine that you have a set of style definitions in a file called `_buttons.scss` in the same directory as your `main.scss` file:

```sass
// filename: _buttons.scss

.button {
    .button-green {
        color: green;
    }
}
```

To include those styles in your `main.scss` file, you would use the `@import` command:

```sass
@import('buttons');
```

This is better than using traditional imports because the files are combined the way you want them to be before they are ever delivered to users. With traditional imports, the files are downloaded separately by the user.

Most of the time, the `main.scss` file becomes an index of imports. It might look something like this:

```sass
// CSS Style Resets
@import('reset');

// Site Components
@import('buttons');
@import('typography');
@import('content_styles');
...
```

To reflect the files mentioned in the example above, your styles directory would look like this:

```ssh
styles/
|-- _buttons.scss
|-- _content_styles.scss
|-- main.scss
|-- _reset.scss
|-- _typography.scss
```

**Please note:** The underscores preceding some of the filenames indicate that those files are "partials". This is a convention in SCSS, so you will see it often. Also notice that you do not need to include the underscore or the `.scss` filename extension in the `@import` statement.

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

* [Getting Started with SASS](http://alistapart.com/article/getting-started-with-sass) by David Demaree
* [The Beginner's Guide to SASS](http://www.webdesignerdepot.com/2013/11/the-beginners-guide-to-sass/) by Andy Leverenz
* [On SASS and Other CSS Preprocessors](https://medium.com/@dannysmith/on-sass-and-other-css-preprocessors-24403fc80b6a) by Danny Smith