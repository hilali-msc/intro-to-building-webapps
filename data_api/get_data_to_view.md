# Put the Data in the View
If you have constructed your `current` data model properly then you should now be able to use it in any Controller to pipe data into your webapp's views. In order to prove out our data integration, we will make a simple form interface so users can look up the weather for their city.

## Set up `MainCtrl` controller in `main.js`
In the file `app/scripts/controllers/main.js` there is a definition for the `MainCtrl` module. This is the module that controls the data and functionality on the main page of our site. We want to get rid of the default code that Yeoman generated for us and replace it with something that looks like this:

```js
angular.module('yourApp')
  .controller('MainCtrl', function ($scope, current) {
    $scope.current = current.query();
  });
```

Let's take a look at this code more closely. First of all, we are once again appending to the `'yourApp'` module, so you'll need to replace that with the name of your app. In the definition of `MainCtrl` we added a few things to the function parameters: `$scope` and `current`. 

As discussed in our previous overview of AngularJS, the `$scope` object is a special AngularJS object that manages the context of the view associated with this controller. The `$scope` object contains all of the variables defined for use in this view, as well as the different functions that can be added to HTML elements inside of our view. We will make extensive use of `$scope` in all of our controllers.

The other parameter references our `current` data model. Now that we've added it to the `MainCtrl` function parameters, we can reference `current` from inside `MainCtrl`. That's exactly what we do on the next line:

```js
$scope.current = current.query();
```

This line sets a variable in `$scope` called `current` equal to the results of the `query()` method on the 