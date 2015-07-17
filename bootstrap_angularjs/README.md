# Bootstrapping an AngularJS Project
Now that we've gotten to know how to use this Yeoman/Bower/Grunt environment, and we have figured out how to add and modify elements (so we can do things like deploy to Github Pages), it's time to get into working with our selected application framework.

For the project we build out in the remainder of this book, we will use the following "stack", or combination of tools and modules:

* AngularJS
* SASS
* Bootstrap CSS/JS Framework

Those are the major components, but we will be using additional elements throughout. We will add `grunt-build-control` again so we can deploy to Github Pages. We will also add several custom AngularJS modules that will be managed using Bower. These modules will help us with things like making sure we maintain accessibility and using the localStorage system to create permanent data storage for users.

In order to get working on our project, we must bootstrap a project skeleton. That involves a few steps.

## Install `generator-angular` for Yeoman
AngularJS has an official generator, which we will make use of. We will install this first.

## Bootstrap an AngularJS project
Once we have the generator installed, we can bootstrap a new project skeleton with Yeoman. This will build out the basic files and templates we will use to build our site.

## Set up SASS
By default, the AngularJS project generator is configured to use a tool called "Compass" to process your SASS styles. Compass is a great tool, but it is a Ruby Gem, which means in order to install it you must have Ruby installed on your computer. If you already use Ruby on projects, it may be much easier to just install Compass and continue with the work.

If you do not already use Ruby, you may prefer to stick with a pure Javascript solution. Since we don't use Ruby anywhere else in this project, this book will show you how to convert your AngularJS app to use SASS instead of Compass, which is set up by the project generator.

## Set up `grunt-build-control`
We will use `grunt-build-control` again to handle deployment to Github Pages. This will be configured pretty much just like we did before, but in order to do that we'll also need to create a Git repo on Github.