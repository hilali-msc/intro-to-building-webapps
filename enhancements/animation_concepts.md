# Animation in AngularJS
In recent versions of AngularJS, the way animating between views is handled has changed significantly. Since we are working with AngularJS above version 1.2, we will focus on the current approach to animating transitions.

In general, when working with Javascript to create dynamic interfaces, it's preferable to use CSS to make animations where possible. The features of CSS that support animation (transitions, keyframes, and animation sequence definitions) are robust and performant. Using Javascript to add/remove classes on HTML elements is a good way to trigger and control animations. By combining Javascript and CSS, you can have a great deal of control over animation.

## Animation basics
Before attempting to work with animations in your AngularJS project, it's good to review the basics of animating with CSS. Animated transitions in AngularJS are triggered by classes that AngularJS applies for you when views change and items are hidden or revealed. Any animation you can define in CSS can be applied to your AngularJS components, and it's very easy to add application-wide animations that happen every time a view changes or content is added to an area of the display.

Animations in AngularJS work best if they are defined as named keyframe animations. These animations can be used inside any style definition, allowing you to define many animations and then use them as you see fit throughout your application. For more background on defining animations in CSS, check out this Mozilla Developers Network page about [Using CSS Animations](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Using_CSS_animations).

## Animate.css
There are many animation toolkits out there for CSS. If you search around, you will have no trouble finding them. One set of CSS animation definitions that I like is the `animate.css` package, which is [available on Github here](https://github.com/daneden/animate.css). The `animate.css` stylesheet defines named keyframe animations that you can then use throughout your project.

Click through to the `animate.css` [Github project page](https://github.com/daneden/animate.css), and you can read a list of the animation names. If you reference those names in your application's stylesheets, you can use those animations. This is an example of what that looks like:

```css
div[ng-view].ng-enter {
    -webkit-animation: fadeIn 0.5s;
    animation: fadeIn 0.5s;
}
```

We will use the `animate.css` package to add animations to our application.

## AngularJS transitions
AngularJS conveniently adds and removes classes on HTML elements as it transitions users through the application. That means we can define styles for those classes that indicate transition states, and those styles may contain animations that will be triggered during a specific part of the transition. In addition, AngularJS conveniently listens to our animations and is smart about removing transition classes after the animation has completed.

It can be tricky at first to work with these transitions because they do not generally show up visibly even in developer tools, but we can see the effects of the transitions if we define proper styles. By learning which classes are applied during which transitions, we can effectively provide animations and styles that work throughout our application and lend a great degree of cohesion to the final product.

The example above indicates that the `fadeIn` animation will be triggered when the `.ng-enter` class is applied to any `<div>` element with an `ng-view` attribute. In practice, that means that any time the AngularJS view changes, this animation will be triggered.

Example of hypothetical app HTML (probably found `app/index.html`):

```html
<div ng-view>
    <!-- This is where the view partial would be inserted -->
</div>
```

And corresponding hypothetical CSS example:

```css
div[ng-view].ng-enter {
    -webkit-animation: fadeIn 0.5s;
    animation: fadeIn 0.5s;
}
```

### AngularJS transition classes
Below is a chart of the classes that are applied during different AngularJS transitions. This chart is based on the information at [Year of Moo](http://www.yearofmoo.com/2013/08/remastered-animation-in-angularjs-1-2.html). [The AngularJS guide to Animations](https://docs.angularjs.org/guide/animations) is also very helpful for learning about how to use animations.

| Action | Starting CSS Class | Ending CSS Class | Directive that fires it |
| -- | -- | -- | -- |
| enter                        | .ng-enter       | .ng-enter-active       | ngRepeat, ngInclude, ngIf, ngView |
| leave                        | .ng-leave       | .ng-leave-active       | ngRepeat, ngInclude, ngIf, ngView |
| move                         | .ng-move        | .ng-move-active        | ngRepeat |
| hide an element              | .ng-hide-add    | .ng-hide-add-active    | ngShow, ngHide |
| show an element              | .ng-hide-remove | .ng-hide-remove-active | ngShow, ngHide |
| adding a class to an element | .CLASS-add      | .CLASS-add-active      | ngClass and class="{{expression}}" |

As you can see, these transition classes are applied every time an item is added or removed from the screen, and you can use these classes to hook onto many different events throughout the user's interaction with your application.

It is useful to note that if you are using named keyframe animations, you only need to apply them on the "Starting CSS Class" -- the "Ending CSS Class" does not need to be defined.

## Getting into it
Of course, the best way to learn about this is to get in and attempt to animate your views. On the next page we will add `animate.css` to our project and use it to apply a general animation to our view changes.