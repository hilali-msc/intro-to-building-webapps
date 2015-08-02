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

Here is what the template should look like after you finish your edits:

```html
<div ng-app class="jumbotron" ng-controller="MainCtrl">
  <h1>Select Your City</h1>
  <p class="lead">
    <div ng-init="location='Seattle'">
        <p>
          <label for="location">Location:
            <input type="text" name="location" ng-model="location">
          </label>
        </p>
        <p>
          <button class="btn btn-lg btn-primary" ng-click="findCities()">Find City</button>
        </p>
    </div>
    <div ng-if="searchQuery">
      <p class="lead">{{citiesFound.count}} cities found matching the query: {{searchQuery}}.</p>
      <dl ng-repeat="city in citiesFound.list">
        <dt>{{city.name}}, {{city.sys.country}}</dt>
        <dd>{{city.weather[0].main}} - {{city.weather[0].description}}</dd>
        <dt>Temperature</dt>
        <dd>{{city.main.temp}} &deg;F</dd>
        <dd><a ng-href="/#/current/{{city.id}}" class="btn btn-lg btn-primary">View Weather</a></dd>
      </dl>
    </div>
  </p>
</div>
```

We use the same text input box and button, but we will attach our `findCities()` function to the button this time. You will notice that we have changed the text label, as well as the text for the title of the page.

We wrapped the results in a `<div>` that is controlled by a `ng-if` directive:

```html
<div ng-if="searchQuery">
```

This directive only shows the element and its children if the conditional contained in the `ng-if` attribute is true. In this case, the results of our search will only show if the `searchQuery` variable contains a value. So when you first load the page, you will see no results, but after you submit your query and the response returns from the API the results will be shown.

Since we anticipate there will be multiple results, we use the `ng-repeat` directive to specify a loop in the `ng-repeat` attribute: 

```html
<dl ng-repeat="city in citiesFound.list">
```

In this case we loop through the `city` objects in `citiesFound.list` Array (which is where the OpenWeatherMap.org API puts the list of cities). Using the `ng-repeat` directive causes the HTML element it's a part of to repeat for every item in an Array.

We output all the different useful information about each city so our user can understand what city has been found. The OpenWeatherMap.org API gives us some brief weather data for each city we found, so we can display some quick, useful information to our users.

Finally, we output a button to click on to view the weather for a given city:

```html
<a ng-href="/#/current/{{city.id}}" class="btn btn-lg btn-primary">View Weather</a>
```

This link makes use of the 


