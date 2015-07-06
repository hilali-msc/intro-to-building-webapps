# Configure `grunt-build-control`
In order to use `grunt-build-control` you will need to configure it. This process involves adding `grunt-build-control` to the list of modules that Grunt knows about, and then configuring a JSON object to define the options and settings we wish to use for our project.

**Please Note:** `grunt-build-control` can be used to deploy to a variety of places. We are only going to explore one method of configuring this tool. Be aware that you may be able to use this tool for other purposes, too.

## Add the `require` statments

First, you must add the proper `require` statements to `Gruntfile.js`. This line should go below the other two require statements in your file, so you should see something like this:

```js
module.exports = function (grunt) {

  // Time how long tasks take. Can help when optimizing build times
  require('time-grunt')(grunt);

  // Load grunt tasks automatically
  require('load-grunt-tasks')(grunt);

  // Load grunt-build-control for deploying this project
  require('load-grunt-tasks')(grunt);

  // Configurable paths
  var config = {
    app: 'app',
    dist: 'dist'
  };
  
  ...
  
```

## Configure the `buildcontrol` task