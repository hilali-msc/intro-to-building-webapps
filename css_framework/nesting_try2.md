# Experimenting with Nesting

As mentioned before, SCSS allows you to use hierarchical nesting structure to create more specific styles. This can help you keep your files more organized (because styles that go together can be contained together), and it helps you overcome any style selector conflicts.

When nesting styles, you may define selectors within selectors. We saw the basic example earlier.

This SCSS:

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
Makes this CSS when it is processed:

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

That is, when the SCSS is processed

