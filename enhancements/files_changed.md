# Files Changed in This Chapter
In order to implement the changes described in this chapter, the following files have been altered. They are quoted below so you can compare your work to a full view of the file.

## `app/views/current.html`

```html
todo
```

## `app/scripts/current.js`

```js
todo
```

## `app/styles/main.scss`

```css
$icon-font-path: "../bower_components/bootstrap-sass-official/assets/fonts/bootstrap/";
@import "variables"; // Override default Bootstrap values.
// bower:scss
@import "bootstrap-sass-official/assets/stylesheets/_bootstrap.scss";
// endbower

@import "content";
@import "buttons";
@import "transitions";
```
## `app/styles/_transitions.scss`

```css
// Styles for animated transitions of HTML elements
div[ng-view].ng-enter {
    -webkit-animation: fadeIn 0.5s;
    animation: fadeIn 0.5s;
}
div[ng-view].ng-leave {
    -webkit-animation: fadeOut 0.5s;
    animation: fadeOut 0.5s;
}
```

## `app/index.html`

```html
todo
```
