# Mixins (Functions)
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