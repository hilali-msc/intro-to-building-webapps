# Exploring Your AngularJS Project
Before we configure your project to deploy, it's worthwhile to take a look at the files in your project and get to know where things are and what's what. Open your project in your favorite text editor so you can browse the files and peek at their content.

If you look at the directory listing of all your files, you'll see something like this:

```bash
.bowerrc
.editorconfig
.gitattributes
.gitignore
.jshintrc
.tmp
.travis.yml
.yo-rc.json
Gruntfile.js
README.md
app/
bower.json
bower_components/
node_modules/
package.json
test/
```

Those files mostly look like the files we had in the webapps we were previously experimenting with. This is because most projects that use a Yeoman template inherit similar-looking structures. This is handy because it makes it easier to learn new tools. 

## Many more modules
If you look inside `bower.json` you will notice there are many more components listed in it than there were in our other webapps. Yours should look something like this:

```json
{
  "name": "yourAppName",
  "version": "0.0.0",
  "dependencies": {
    "angular": "^1.3.0",
    "bootstrap-sass-official": "^3.2.0",
    "angular-animate": "^1.3.0",
    "angular-aria": "^1.3.0",
    "angular-cookies": "^1.3.0",
    "angular-messages": "^1.3.0",
    "angular-resource": "^1.3.0",
    "angular-route": "^1.3.0",
    "angular-sanitize": "^1.3.0",
    "angular-touch": "^1.3.0"
  },
  "devDependencies": {
    "angular-mocks": "^1.3.0"
  },
  "appPath": "app",
  "moduleName": "yourAppName",
  "overrides": {
    "bootstrap": {
      "main": [
        "less/bootstrap.less",
        "dist/css/bootstrap.css",
        "dist/js/bootstrap.js"
      ]
    }
  }
}
```

Remember that we want to let Bower manage this file, so we won't edit it by hand. But looking in the `bower.json` file on a project is a great way to start to understand what components are involved.

Looking inside `package.json` is another way to see what is being used in a project. This file will list a whole different set of resources. We will interact more directly with many of these components throughout our work on this project.

## App structure
Inside the `app/` directory is where all the code for your webapp is stored. If you look at the structure within that directory, you will see something like this:

```bash
.buildignore
.htaccess
404.html
favicon.ico
images/
|----yeoman.png
index.html
robots.txt
scripts/
|----controllers/
|--------about.js
|--------main.js
|----app.js
styles/
|----main.scs
views/
|----about.html
|----main.html
```

We will work within this structure for the rest of the book. The `styles` directory will work pretty much like it did in our previous webapp experiments. We will likely want to copy over the Bootstrap _variables.scss file and set up some partial stylesheets. We will work on that in the next chapter. For now we will leave the styles as-is.

Note that the `index.html` file still provides the starting point for a browser to interact with our webapp. This page is loaded first, and you will find that it still must set up the basics for viewing the page: It defines a viewport, doctype, sets up meta tags, and includes our scripts and styles. This looks a lot like the `index.html` file we used in our previous experiments, but the difference now is that most of our work in AngularJS will take place in our `views`, which are partial templates. This `index.html` file will rarely be touched once it's all set up.

The `scripts` directory is where much of our work will take place. This is where all the Javascript we write for our app goes. By default we have an `app.js` file, which defines our application for AngularJS. The `app.js` file is used in several different ways, and we'll explore that a lot more over the coming chapters.

Also in the `scripts` directory is a `controllers` sub-directory. The `controllers` are what handles manipulating data and setting up the Javascript functions that are available to our `views`. By default, the Yeoman generator has set us up with two views: `about` and `main`. These two views each have a unique controller, so within the `scripts/controllers/` directory we find two corresponding Javascript files.

Finally, we come to the `views` directory. Inside are two `.html` files. If you look inside those `.html` files you will notice that they are not actually entire HTML documents. They are, in fact, "partials" -- meaning that they are partial HTML templates. This is what AngularJS uses to render new HTML into the overall single page app structure. These parts of HTML files will be brought into our `index.html` file as the user interacts with our app.

The best way to get a feel for how this is going to work is to make a few changes and see. So that's what we'll do next.


