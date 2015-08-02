# Wiring Up `citysearch` on the Home Screen
Now that we've got the `citysearch` resource defined, let's try it out. In order to do that, we will need to alter the `MainCtrl` Controller (in `main.js`) and the `main.html` template. We will set it up so that we use the existing text input and button on the home screen, but instead of immediately calling the `current` resource, we will show the list of cities we have found so the user may select one.

## Set up `MainCtrl` in `main.js`
In order to search for cities on the home screen, we must use the `citysearch` resource in the `MainCtrl` Controller. We must also rework the way we assign variables and set up our refresh function. Here is what your `MainCtrl` object should look like after you finish your edits:

```js
angular.module('yourApp')
  .controller('MainCtrl', function ($scope, citysearch) {
    $scope.citiesFound = citysearch.find();

    $scope.findCities = function(){
        $scope.citiesFound = citysearch.find({
            query: $scope.location
        });
        $scope.searchQuery = $scope.location;
    };
  });
```

You will notice that we are now using `$scope` and `citysearch` in this controller. We have create a `$scope` variable called `citiesFound` that we can use to loop through the results of our search. We initialize that value to the results of a default search. We also define a `$scope` function called `findCities()`, which performs a search and updates a `$scope` variable called `searchQuery`. This `$scope.searchQuery` variable is an example of the kinds of variables you can use to improve the user interface. We will store the value of `$scope.location` that we searched for so that we can provide good feedback to our user about the search results.

There is not too much code here, and for the most part it is not very different from the code we wrote to fetch the current weather. Hopefully these lines are starting to feel familiar and you're gaining some comfort with some of these common patterns.

## Set up the `main.html` template
Now that we have the `MainCtrl` Controller all ready to power our view, we need to set up our template. This is also a fairly straightforward conversion, although you will probably want to pull up some sample queries in Postman or another API browser so you can get an idea of the data structure you receive when using the Find API. This is different, but similar to, from the structures returned by the Current Weather API.

