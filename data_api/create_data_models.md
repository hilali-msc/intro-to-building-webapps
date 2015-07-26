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

The factory we made is for the `current` data model. This model will contain the data for the "current weather" at a given location. This model will NOT contain the data for the "weather forecast" at a given location (that would be defined as another data model and factory service).

## Configure your resource
Now that you have a `current` factory service in `app/scripts/services/current.js`, you need to add some logic to it so it does something. By default, the service that has been generated looks like this:

```js
angular.module('yourApp')
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
We want to replace this with code that connects to our chosen API service. The file `app/scripts/services/current.js` should look like this:

```js
angular.module('yourApp')
  .factory('current', function ($resource) {
    // Service logic
    // ...

    // Public API here
    return $resource('http://api.openweathermap.org/data/2.5/weather?q=:location&units=imperial&APPID=YOUR_API_KEY_HERE', {}, {
      query: {
        method:'GET',
        params:{
          location: 'Seattle,us'
        },
        isArray:false
      }
    });
  });
```

Let's take apart what's happening in that factory definition. First of all, you can see that we access the base `angular` object, and the `module()` method. We specify our app module: `yourApp`. Alter that to match with the name of your app.

This factory is named `'current'` and you can see that the function definition takes in `$resource` as a parameter. This is how we refer to the `ngResource` module within our Javascript code. This module provides us with the ability to write the `$resource` statement that we are returning as the "Public API". 

First, we specify the base API URL. We can replace parts of this URL with variable names. In this case, I have replaced the actual "query" with `:location`. We could, for example, also replace the `units` value with a variable name so we could allow our users to switch between Metric and Imperial units.

**Please also note that you must replace YOUR_API_KEY_HERE with your actual API key from OpenWeatherMap.org.**

Once we have defined the base API URL, we can move on to specify a Javscript `object` that will contain all of the methods we wish to define as part of our `current` data model. By specifying a `query` object here, we are allowing ourselves to use the `query()` method on the `current` model. So when we use the `current` model in a Controller we can write:

```
current.query({location: 'Chicago,us'});
```
That line would query the OWM API service for the current weather in Chicago.

The `query` object in our `$resource` definition specifies a few other things, too:

```js
query: {
    method:'GET',
    params:{
      location: 'Seattle,us'
    },
    isArray:false
}
```

The HTTP method that will be used to make the API request is GET, which is appropriate since this is a "read only" service. (We cannot alter the weather via API call... yet!) We also let AngularJS know that we do NOT expect these results to be a Javascript Array (as opposed to an Object) by setting `isArray:false`.

The interesting part of the `query` definition is the `params` object. The `params` object allows us to specify default values to be filled in if the `query()` method is called without those params specified. In this case, we are supplying `'Seattle,us'` as the `location` value so that when the query is run with no parameters it still returns results. This is a useful way of providing user-friendly defaults and minimizing the likelihood for your app to break if not all params are specified.

If you wish for a param to be left blank if it is not supplied you can set the default to be equal to `null`:

```js
params: {
    location: 'Seattle,us',
    bogus: null
}
```

## Now what?
Now that you have your `$resource` defined as a factory service, you can use this `current` data model in any view you choose by adding the `current` service to your AngularJS Controller parameters. We will do that next.