# Create Data Models
In order to use the data from our API in our webapp, it is necessary to create data models. There are several way to accomplish this goal, but we will explore a technique that is both commonly used and well-suited to our needs. We will use the `ngResource` module to create a connection between our data API and the data we use in our views.

We will use the Yeoman `generator-angular` module to create stub files of Angular Services and Controllers. By using the Yeoman generator, we will have an easier time of making sure that all of our source files are being properly included in our application.

**If you use the tools to help maintain your dependencies, then you will have a much easier time. If you choose to edit files directly you may find yourself getting errors and running into issues more often.**

As you move through these steps, realize that you can repeat this process for as many API objects as you wish to use in your app. You can create resources that talk to entirely different APIs if you wish. Each resource represents a unique stream of data into a model that you can use in any of your application's views.

## Generate a factory service
In order to manage data from the server, we will use a "factory service". That is, we will create an AngularJS Service using the `factory()` method. To generate this service, you will need to use the command line `yo` application. Use `cd` to change directory into your project root (the same directory as your `Gruntfile.js` is located).

Once you're in the correct location, run the following command and you should see similar results:

```
$ yo angular:factory current
    create app/scripts/services/current.js
    create test/spec/services/current.js
```
That command asks the Angular generator to create a new factory service in your app. It makes two files and adds references to those files in the appropriate places (including your `index.html`).

## Configure your resource
Now that you have a `current` factory service, you need to add some logic to it so it does something. By default, the service that has been generated looks like this:

```js
angular.module('weatherApp')
  .factory('current', function () {
    // Service logic
    // ...

    var meaningOfLife = 42;

    // Public API here
    return {
      someMethod: function () {
        return meaningOfLife;
      }
    };
  });
```
We want to replace this with code that connects to our chosen API service.
