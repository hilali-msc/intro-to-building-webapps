# Bootstrap a Test Project
In order to get used to all the pieces of our new develpment environment, we will create a simple test project based on a common Yeoman generator template. The `generator-webapp` template puts the key pieces of the Yeoman Workflow into place, giving you an HTML file, Javascript files, SASS support, and more.

Getting this project up and running is not too difficult. First, you should open your terminal and change directory into whatever directory you cloned your test Github repository into. 

Run the following command to generate a project skeleton based on `generator-webapp`:

```bash
yo webapp
```

You should see the following information display:

![Yo webapp generator](img/yo-webapp-gen.png)

Many Yeoman generators allow developers to select optional components and features. In this case, the generator is asking us if we want to use the [Bootstrap CSS Framework](http://getbootstrap.com), [SASS CSS](http://sass-lang.com/) Preprocessor, and [Modernizr](http://modernizr.com/), a Javascript polyfill that makes HTML5 sites work better on old browsers.

We want all of those in our project, so use the `up` and `down` arrow keys to move through the list, and the `spacebar` to select each option. Make sure each option has a bright green dot next to it. Once you've selected all the options, press `enter` to move on.

In some cases, you will need to answer additional questions. Whenever you use SASS, generators will often offer you the option of using a module called `node-sass` instead of the SASS Ruby Gem. Unless you have consciously installed the Ruby Gem, it's advisable to use `node-sass`, so when it asks us this question, we will say "y", we want to use `node-sass`.

![Do you want to use node-sass?](img/webapp-step2.png)

Press `y` and then `enter` to begin the build.

