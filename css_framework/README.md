# Getting to Know Your CSS Preprocessor
Over the past several years, frontend developers have embraced CSS Preprocessors&mdash;tools that allow you to write and manage your CSS with more functionality. 

CSS Preprocessors address three major issues when writing styles, adding functionality on top of normal CSS functions: How do we better organize our styles (both inside a single file and across multiple files)? How do we handle configuration data and re-used components? How do we ease the pain of repetitive sequences of style definitions?

There are many other doors that open and problems that are solved by trying to solve these three base issues. 

For our project, we are using a CSS Preprocessor called `node-sass`, which allows us to use ["SASS"](http://sass-lang.com) (Syntactically Awesome Style Sheets). SASS, the specification, has been implemented into several different preprocessor tools (such as `node-sass` or the `sass` Ruby Gem). SASS and SCSS (Structured CSS) are terms that tend to be used interchangeably. Technically, SCSS is the piece that adds the hierarchical (nested) capabilities, while SASS is the specification that adds imports, variables and mixin capabilities.
