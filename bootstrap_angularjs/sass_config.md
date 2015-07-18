# Configure SASS 
In order to run the server on your site, Grunt will need to build your stylesheets. Unfortunately, the `generator-angular` template forces us to set up the project to use [Compass](http://compass-style.org/). Compass is a great CSS preprocessor, but it has one downside for us here: It requires us to use Ruby. If you already have Ruby installed, or if you're interested in working on Ruby projects, feel free to [install Compass](http://compass-style.org/install/) and continue using Compass. Compass will give you additional features you can leverage that we won't cover in this book.

Since we have no dependencies outside of Javascript for our work here, we will use a Node.js module called `grunt-sass` to process our CSS. This uses a pure-Javascript SASS processor to provide speedy, high quality treatment of our `.scss` files. 

(Note: The approach here mimics the approach described by Ravel Antunes in [his article](http://ravelantunes.com/blog/angular-generator-libsass/).)

## Install `grunt-sass`
Installing `grunt-sass` is the same as installing any Node.js module into your project. We will use `npm` and we will send the `--save-dev` flag to save this into our `devDependencies` list.

```
npm install --save-dev grunt-sass
```

## Configure `Gruntfile.js`
We must remove the configuration for the `compass` task and add new configurations for a `sass` task in our `Gruntfile.js`. This will involve changing Gruntfile.js in several places. Pay close attention to where you are making edits. If you mix up a curly brace or a comma, you'll get errors when you run `grunt` commands.

### Configure `sass` task
Remove this `compass` config:

```js
// Compiles Sass to CSS and generates necessary files if requested
compass: {
  options: {
    sassDir: '<%= yeoman.app %>/styles',
    cssDir: '.tmp/styles',
    generatedImagesDir: '.tmp/images/generated',
    imagesDir: '<%= yeoman.app %>/images',
    javascriptsDir: '<%= yeoman.app %>/scripts',
    fontsDir: '<%= yeoman.app %>/styles/fonts',
    importPath: './bower_components',
    httpImagesPath: '/images',
    httpGeneratedImagesPath: '/images/generated',
    httpFontsPath: '/styles/fonts',
    relativeAssets: false,
    assetCacheBuster: false,
    raw: 'Sass::Script::Number.precision = 10\n'
  },
  dist: {
    options: {
      generatedImagesDir: '<%= yeoman.dist %>/images/generated'
    }
  },
  server: {
    options: {
      sourcemap: true
    }
  }
},
```
And replace that entire configuration with this new configuration:

```js
// Compiles Sass to CSS and generates necessary files if requested
sass: {
    options: {
        includePaths: [
            'bower_components'
        ]
    },
    dist: {
        files: [{
            expand: true,
            cwd: '<%= yeoman.app %>/styles',
            src: ['*.scss'],
            dest: '.tmp/styles',
            ext: '.css'
        }]
    },
    server: {
        files: [{
            expand: true,
            cwd: '<%= yeoman.app %>/styles',
            src: ['*.scss'],
            dest: '.tmp/styles',
            ext: '.css'
        }]
    }
},
```

### Update `watch` task by adding a `sass` sub-task
Look for the `watch` task definition, which contains a list of things that `grunt` runs while it is running the development server. This task is what defines which files get watched for changes and what happens when a change is detected.

Within the `watch` task definition, find the `compass` sub-task:

```js
compass: {
    files: ['<%= yeoman.app %>/styles/{,*/}*.{scss,sass}'],
    tasks: ['compass:server', 'autoprefixer:server']
},
```
Replace that definition with a new `sass` sub-task:

```js
sass: {
    files: ['<%= yeoman.app %>/styles/{,*/}*.{scss,sass}'],
    tasks: ['sass:server', 'autoprefixer']
},
```

### Update the `concurrent` task
Finally, locate the `concurrent` task definition. This task defines things that should happen simulatneously in order to speed up processing and building files. This is part of what makes the dev environment so fast.

The current `concurrent` task config looks like this:

```js
// Run some tasks in parallel to speed up the build process
concurrent: {
  server: [
    'compass:server'
  ],
  test: [
    'compass'
  ],
  dist: [
    'compass:dist',
    'imagemin',
    'svgmin'
  ]
},
```
Replace that config with a new `sass` config:
```js
// Run some tasks in parallel to speed up the build process
concurrent: {
  server: [
    'sass:server',
    'copy:styles'
  ],
  test: [
    'copy:styles'
  ],
  dist: [
    'sass',
    'copy:styles',
    'imagemin',
    'svgmin'
  ]
},
```

## Test your project
Now that you've updated `grunt` to use `grunt-sass` instead of `compass`, you can try out your new project. Run `grunt serve` to view your project in a web browser. You should see something like this:

