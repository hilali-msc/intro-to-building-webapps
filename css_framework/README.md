# Getting to Know Your CSS Preprocessor
Over the past several years, frontend developers have embraced CSS Preprocessors&mdash;tools that allow you to write and manage your CSS with more functionality. CSS Preprocessors address three major issues when writing styles, adding functionality on top of normal CSS functions: How do we better organize our styles (both inside a single file and across multiple files)? How do we handle configuration data and re-used components? How do we ease the pain of repetitive sequences of style definitions?

There are many other doors that open and problems that are solved by trying to solve these three base issues. 

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

Imagine that you have a set of style definitions in a file called `_buttons.scss`:

```sass
// filename: _buttons.scss
```


## Variable Definition

## Mixins (Functions)