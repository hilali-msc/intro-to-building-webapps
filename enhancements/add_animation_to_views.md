# Animating View Transitions
In order to provide a more visually compelling experience for our users, and to reinforce when data in our app changes, we will create some view transition animations. We will take a fairly simple approach here, but you are encouraged to continue experimenting and using this same basic process to add more animations to different changes throughout your app. Keep in mind that you can animate any transition that happens in your application.

## Add `animate.css` to the project
In order to create our animations, we will use an open source animation library called `animate.css`. You may reference the [`animate.css` Github repository](https://github.com/daneden/animate.css) to see what animations are included.

To add `animate.css` to the project, we will use Bower. As usual, you will need to open your terminal and change directory into your project directory. Once you are in your project root, run the following command:

```bash
bower install --save animate.css
```

Bower should successfully install `animate.css` and add it to our `app/index.html` file:

```html
<!-- bower:css -->
<link rel="stylesheet" href="bower_components/animate.css/animate.css" />
<!-- endbower -->
```

Now that you've installed `animate.css` as a CSS dependency in your app, you can reference the animations defined in the CSS library. (Again, look at the Github repository page for a list of animations.)

## Define animations
In order to keep my stylesheets nice and tidy, I like to define transition animations in their own stylesheet. In order to do that, I will add an import statement to my `app/styles/main.scss` so my transition styles will be properly included.

Here is the line I added to `app/styles/main.scss`:

```css
@import "transitions";
```

And then I will create a new file located at `app/styles/_transitions.scss`. Inside this file, I will put a style definition to create a transitional animation for every time the view changes.

The contents of `app/styles/_transitions.scss` look like this:

```css
div[ng-view].ng-enter {
    -webkit-animation: fadeIn 0.5s;
    animation: fadeIn 0.5s;
}
div[ng-view].ng-leave {
    -webkit-animation: fadeOut 0.5s;
    animation: fadeOut 0.5s;
}
````

This is almost the same example from the previous page, and as we mentioned before, this style will make it so our content fades in