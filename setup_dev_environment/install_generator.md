# Install a Generator
In order to test out our development environment, we should install a "generator". Generators are Node modules that tell Yeoman how to build out a project skeleton. There are many generators. You can find a [searchable index on the Yeoman website](http://yeoman.io/generators).

For our purposes, the Webapp generator will suffice. To install it, run the following command in your terminal:

```bash
npm install -g generator-webapp
```

Remember that NPM is the package manager that came with Node. That command tells your system to install the `generator-webapp` module. The `-g` flag tells it to install the module "globally" -- so it is available to run anywhere on your system.

Once that process finished running, you will be able to generate a new project skeleton based on the `generator-webapp` template.