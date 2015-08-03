# Store and Retrieve Locations
Most weather apps and websites allow you to store a list of your preferred locations so you can easily refer to them when you return to the app. We will allow our users to store their chosen locations and then access those cities in a list on the home screen of our location. They can then click into one of the cities from their list, or they can search for other cities.

## Add the ngStorage module
In order to use the `localStorage` feature of modern web browsers, we will install the [ngStorage](http://ngmodules.org/modules/ngStorage) module for use in our project. This will make the `$localStorage` object available to our controllers so we can use locally stored data easily throughout our application.

We install ngStorage with Bower:

```bash
bower install --save ngstorage
```

You may notice that running this command adds a line to your `app/index.html` file with a `<script>` tag pointing to the ngStorage file. In addition to that, we must manually add the `ngStorage` module to our list of required modules in our app definition (which is in `app/scripts/app.js`). The first part of your app definition should look like this after you add the `ngStorage` module:

```js
angular
  .module('test3App', [
    'ngAnimate',
    'ngAria',
    'ngCookies',
    'ngMessages',
    'ngResource',
    'ngRoute',
    'ngSanitize',
    'ngStorage', // added to enable localStorage features
    'ngTouch'
  ])
  .config(function ($routeProvider) {
  //  ... additional code...
```

This addition makes the ngStorage Javscript module and it's components available in our application, but we must still let our controllers and other object know about the object before they use it.

## Modify the `CurrentCtrl` Controller
The `CurrentCtrl` Controller is the controller in charge of rendering our current weather view in the `app/views/current.html` template. This controller will be used to "save" our city. In order to add a "save" button to the template, we need to make a function that will add the city to our 