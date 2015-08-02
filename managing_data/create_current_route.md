# Creating the `current` Route
To create a route for our "current weather" view, we will use the Yeoman generator once again. This time, we will run the following command in our project:

```ssh
yo angular:route current
```

This command will create a controller called `CurrentCtrl` in `app/scripts/controllers/current.js` and a template called `current.html` in `app/views/current.html`. It will also add this entry to your `app/scripts/app.js` file:

```js
.when('/current', {
    templateUrl: 'views/current.html',
    controller: 'CurrentCtrl',
    controllerAs: 'current'
})
```

We will need to alter this route in one small way to get things working. We will add a "router parameter" called `:cityID` to the path for this route. That router parameter is something we can pick up in our controller, so we can use that information to change the response this view delivers.

Here is how your route definition will look after you add that parameter:

```js
.when('/current/:cityID', {
    templateUrl: 'views/current.html',
    controller: 'CurrentCtrl',
    controllerAs: 'current'
})
```