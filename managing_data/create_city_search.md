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

