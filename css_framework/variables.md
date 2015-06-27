# Variables
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