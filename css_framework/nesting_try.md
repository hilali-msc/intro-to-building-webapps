# Nesting and Imports: Set Up Your Stylesheets

In order to make the most of our new CSS preprocessor, let's set up our stylesheets for further development. We need to establish our file structure and set up our imports to allow us to write clean, well-organized code that makes the most of the SCSS nesting capabilities to create an obvious hierarchy.

## Locate your stylesheet
As we saw when we bootstrapped the site, the stylesheets for our project are located at `app/styles/`. As part of the bootstrapping process, a `main.scss` file was created and some styles were added there to support the project skeleton homepage.

Open `app/styles/main.scss` and observe the styles that have been pre-created for you. There is a `.browsehappy` style, which is an element that shows up when outdated browsers hit your page. (You can find that element, and the code that makes it appear,  in the `app/index.html` file.)

You will also see several styles that affect the content inserted into `app/index.html` for demonstration purposes. These show you how SCSS can be written, and you should start editing with just altering some of the values to experiment.

If you are running your server as you edit, you should see your page automatically update in the browser whenever you save your changes. This can be very handy for rapidly working on style definitions. Of course, what's happening is that when you run `grunt server`, there is a `watch` task that runs. The `watch` task monitors files in your app for changes, and when a change is detected it kicks off the whole build process. 

Pretty neat, right?

So although these style definitions are useful (you might also pay special attention to the way they write their media query to target mobile devices), they are not necessary. You may remove any of the styles that you wish. In general, it's not recommended to put styling directly into your `main.scss` stylesheet.

## Setting up your `main.scss`

