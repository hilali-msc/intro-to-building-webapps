# Customizing Variables

Since we're already working with Bootstrap, it makes sense to leverage as much of it as possible. This is only possible if we use the `_variables.scss` file to customize the variable values for our project.

The values in `_variables.scss` control everything from the color palette for the site, the font families and type settings that are used for your site, default style settings for buttons, inputs, and even the specific dimensions at which the Bootstrap grid will break down for different screen sizes.

## Colors

The first section of the `_variables.scss` file defines colors. Notice the way the gray colors are defined:

```sass
$gray-darker:            lighten(#000, 13.5%) !default; // #222
$gray-dark:              lighten(#000, 20%) !default;   // #333
$gray:                   lighten(#000, 33.5%) !default; // #555
$gray-light:             lighten(#000, 46.7%) !default; // #777
$gray-lighter:           lighten(#000, 93.5%) !default; // #eee
```

First of all, variables in SASS begin with a dollar sign (`$`). Second, these color definitions are using the `lighten()` mixin. There is usually not much reason to change the gray values, but you are free to do so if you wish.

The next set of definitions is much more impactful for branding our site:

```sass
$brand-primary:         #428bca !default;
$brand-success:         #aa0000 !default;
$brand-info:            #5bc0de !default;
$brand-warning:         #f0ad4e !default;
$brand-danger:          #d9534f !default;
```

You may alter these colors however you desire. You can use hex codes to define the color, or `rgb()` and `rgba()` style definitions. You may also use the `lighten()` and `darken()` mixins.

## Typography

The next section of `_variables.scss` worth noting is the Typography section. This defines the way fonts look on your site. The main font definitions come first:

```sass
$font-family-sans-serif:  "Helvetica Neue", Helvetica, Arial, sans-serif !default;
$font-family-serif:       Georgia, "Times New Roman", Times, serif !default;
//## Default monospace fonts for `<code>`, `<kbd>`, and `<pre>`.
$font-family-monospace:   Menlo, Monaco, Consolas, "Courier New", monospace !default;
```

You may alter these to use whatever fonts you have available (including any font you have made available through a webfont method like Typekit, Google Fonts, or just a regular old `font-face` definition).

In addition to the fonts themselves, you'll find the following two variables, which are important for dicating how type appears on your site:

```sass
$font-size-base:          14px !default;
$line-height-base:        1.428571429 !default; // 20/14
```

These values modulate many aspects of how your site appears. If you generally want to increase or decrease the size and spacing of your fonts, you should make those changes here, in the `_variables.scss` file.

## Additional Variables

The `_variables.scss` file is very long and defines many settings for Bootstrap. If you want to play with these in a more interactive format, the [Bootstrap Live Customizer](http://bootstrap-live-customizer.com/) tool is a great way to see the effect your variable changes can have on a theme.

Whenever you find yourself working against Bootstrap, it's worthwhile to check if the thing you're trying to do could be accomplished by modifying a variable. Often developers find themselves working against their frameworks because they do not realize the flexibility that has been built into the system. Take the time to get to know some of these options and play with making changes to see how you can affect the look and feel of your site.