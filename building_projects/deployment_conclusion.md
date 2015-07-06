# Après Deployment
Now that you've deployed your project, when you visit the URL shown in our Github Pages Settings box, you should see something like this:

![Demo project deployed!](img/demo-deployed.png)

This shows the changes we made in the last chapter to everyone. If you inspect this deployment you will see several things that are different from when you normally preview your site using your local server.

## File combination and versioning

## Minification
All HTML, CSS and Javascript is "minified" when we deploy. This means that extra spaces, linefeeds, and other formatting niceties are removed to make the file as small as possible. In some situations it might even involve rewriting the names of variables or functions to be shorter and smaller. There are many ways that minification helps compress files to make them as small as possible so they can be delivered to our users as quickly as possible.

Here is an example of what HTML looks like after it has been minified:

![Minified HTML](img/minified-html.png)

If you use the "Inspect Element" tool in your browser, then you will still see the HTML broken into a nice visual display, but that's because the developer tools are able to reformat the HTML. When you view source, you will see the compressed HTML like you see above.

## More
More happens when we build the site, too. Tests are run. If they fail, it will cause us issues. Fortunately, we have no tests written, so that cannot prevent us from deploying. But when we get around to adding tests to our project, that will be a great way to help us not make a mistake by deploying broken code.

Grunt is also looking at all of our images and trying to optimize those. Right now we are not using any images, but if we did then they would be optimized and compressed as much as possible before deployment. This is a good thing for our users.

There are many other things that Grunt can do for us as part of the build and deployment process. As you encounter challenges in your development, keep in mind the things Grunt can do for you and on the lookout for opportunities to get more out of a tool you're already using.