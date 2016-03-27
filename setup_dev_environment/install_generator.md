# Install a Generator
To test out our development environment, we should install a "generator". Generators are Node modules that tell Yeoman how to build out a project skeleton. There are hundreds of generators available. You can find a [searchable index on the Yeoman website](http://yeoman.io/generators).

For our purposes, the Webapp generator will suffice. To install it, run the following command in your terminal:

```bash
npm install -g generator-webapp@1.1.2
```

Remember that NPM is the package manager that came with Node. That command tells your system to install the `generator-webapp` module. The `-g` flag tells it to install the module "globally" -- so it is available to run anywhere on your system.

Once that process finished running, you will be able to generate a new project skeleton based on the `generator-webapp` template.

**Please Note:** The latest version of the `generator-webapp` module was recently redesigned to use a task manager called `Gulp`. This book will eventually be updated to catch up to the switch to `Gulp` but for a variety of reasons it's beneficial to stick with `Grunt` for now. (`Grunt` is still used by the other generator we will use throughout this book, the `generator-angular` module.)