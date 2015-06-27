# Making the Most of Mixins

Mixins are powerful tools, and you should consider them in two ways:

1.  You can create a mixin to handle any repetitive code generation task that can be defined with logic. The mechanisms provided to create, essentially, "CSS functions" are very handy.
2.  You can use mixins created by others, and if you're working with a CSS framework, then it is likely to offer you mixins to use.

Since we're working with Bootstrap, we have lots of mixins at our disposal. We can learn from them. We can also take existing mixins and modify functionality to create our own.

## Organizing mixins
Most of the time, we keep mixins in a separate file (or multiple files) so we don't get them lost in our stylesheets. Bootstrap stores its mixins in a `mixins/` directory containing many files.

You should be able to find the Bootstrap mixins directory in your project in:

```bash
bower_components/bootstrap-sass-official/assets/stylesheets/bootstrap/mixins/
```

