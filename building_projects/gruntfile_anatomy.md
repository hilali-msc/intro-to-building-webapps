# Anatomy of a Gruntfile
We use the file `Gruntfile.js` to configure Grunt tasks. Tasks are specific commands we can run using Grunt. We can configure tasks with whatever names we want, and we can combine tasks however we want, so there is a lot of flexibility in terms of what we can do with Grunt to help us accomplish more with our development processes.

## Grunt is JS
The first thing to remember as you are editing your `Gruntfile.js` is that, as the filename extension indicates, this is a Javascript file. You need to obey the rules of Javascript and have your Javascript hat on when dealing with Grunt configurations. Trailing commas, loose management of curly braces, and bad use of quotes can cause you to have syntax errors just like any other piece of Javascript. Although we don't typically do a bunch of logic in the `Gruntfile.js`, it's still a Javascript file.

## Organization of `Gruntfile.js`
The Grunt configuration begins on the line that starts:

```module.exports = function (grunt) {```

This entire file is exporting a `function` that can be executed by Grunt. Inside this function, we declare some variables, include some additional modules via `require` statements, and then initialize Grunt with a configuration that defines all of our tasks.

Starting right below the `module.exports` line, you should see a couple of require statements:

```js
// Time how long tasks take. Can help when optimizing build times
require('time-grunt')(grunt);

// Load grunt tasks automatically
require('load-grunt-tasks')(grunt);
```

Those lines are telling Grunt that we are also using these other Node.js modules. (Later on we will add `grunt-build-control` to the list.)

Below those lines comes the declaration of the `config` variable:

```js
// Configurable paths
var config = {
    app: 'app',
    dist: 'dist'
};
```

This variable is crucial for Grunt, especially in our context. We are telling Grunt where our application is located as well as the name we wish to use to contain the built website files. These two definitions are used throughout the configuration of the other tasks in the Grunt file.

Finally, we come to the beginning of how we will configure our Grunt tasks, using the `grunt.initConfig()` method:

```js
// Define the configuration for all the tasks
grunt.initConfig({
    // Project settings
    config: config,
```

All of the rest of this file exists within that `grunt.initConfig()` call. What follows is a massive JSON object defining all the settings for the different tasks we are using in our project. You can see the different commands we run on the command line and how they are configured. 

## Task definitions
For the most part to truly understand what each configured task is doing, and how to modify the functionality, it's essential to actually visit the documentation for that module and learn about the configuration options. Each module is configured slightly differently.

As an example of what a task configuration looks like, we can look at the default `mocha` task definition created as part of the project template:

```js
// Mocha testing framework configuration options
mocha: {
  all: {
    options: {
      run: true,
      urls: ['http://<%= connect.test.options.hostname %>:<%= connect.test.options.port %>/index.html']
    }
  }
},
```

Mocha is the test running library being used in this project. This module allows you to run any tests you've created to verify the functionality of your website. The specifics of this module are not important here since we are just looking at what the configuration looks like. 

You can see that the tasks are referenced by the "key" in the JSON object, so this task would be run with `grunt mocha` if you wanted to run it all alone. `mocha` references an object that contains the configuration for the `mocha` module in a structure that has been defined by the developers who created the `mocha` module.

You can note that in the definition of the `urls` property, the configuration specifies an array of strings. Those strings are leveraging a templating format that is allowed inside Grunt configurations. This templating allows us to reference the values of other Grunt tasks or components, or even the `config` object that we defined previously. 

## Getting comfortable
Read through the task definitions and try running some of the tasks on their own in your console. Some of them will not work properly when run alone because they need to work as a part of a bigger sequence. For example, in practice we would probably never run `grunt mocha`, but we would run `grunt test`, which in turn references and executes the `grunt mocha` task.

Note that the `copy` task is the task that controls copying files into your final build. You may, for example, discover that if you need to add a subdirectory to your project, you will need to specify that directory to be copied, too. For performance and control reasons, we typically write our `Gruntfile.js` files to be very specific about what to copy and where. When you add to or alter your projects file structure you will likely need to update some of these configurations. 

Spending a little time reviewing and experimenting with these pre-existing Grunt tasks is a great way to get comfortable with this tool. You can do a lot with it, so keep it in mind when you encounter troubles or discomfort in your development process.