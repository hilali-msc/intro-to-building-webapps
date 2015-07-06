# Anatomy of a Gruntfile
We use the file `Gruntfile.js` to configure Grunt tasks. Tasks are specific commands we can run using Grunt. We can configure tasks with whatever names we want, and we can combine tasks however we want, so there is a lot of flexibility in terms of what we can do with Grunt to help us accomplish more with our development processes.

## Grunt is JS
The first thing to remember as you are editing your `Gruntfile.js` is that, as the filename extension indicates, this is a Javascript file. You need to obey the rules of Javascript and have your Javascript hat on when dealing with Grunt configurations. Trailing commas, loose management of curly braces, and bad use of quotes can cause you to have syntax errors just like any other piece of Javascript. Although we don't typically do a bunch of logic in the `Gruntfile.js`, it's still a Javascript file.

