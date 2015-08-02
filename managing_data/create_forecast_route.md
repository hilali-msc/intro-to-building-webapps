# Creating the `forecast` Route and View
Creating the forecast view is almost identical to creating the current weather view. The two start with the same basic Yeoman command:

```bash
yo angular:route forecast
```

Once you've run that command you should be able to see the controller file (`app/scripts/controllers/forecast.js`), view template (`app/views/forecast.html`) and the changes inside of `app/scripts/app.js`:

```js
.when('/forecast', {
    templateUrl: 'views/forecast.html',
    controller: 'ForecastCtrl',
    controllerAs: 'forecast'
})
```

Once again, we will modify that route definition so it will accept a route parameter called `cityID`:

```js
.when('/forecast/:cityID', {
    templateUrl: 'views/forecast.html',
    controller: 'ForecastCtrl',
    controllerAs: 'forecast'
})
```

Now that we have `cityID` coming through as a route parameter, we can set up the `ForecastCtrl` Controller.

## Edit `ForecastCtrl` Controller
As we did with the `CurrentCtrl` Controller, we will set up our `$scope` variables so we can display our desired data in the `forecast.html` template. The controller will end up looking very much like the `CurrentCtrl` Controller:

```js
angular.module('yourApp')
  .controller('ForecastCtrl', function ($scope, $routeParams, forecast) {
    $scope.cityID = $routeParams.cityID;

    $scope.forecastData = forecast.query({
        cityID: $routeParams.cityID
    });
  });
```

This is almost identical to the controller for the current weather view. The two views ultimately perform the same task: They both accept a `cityID` and then make a query to the OpenWeatherMap.org API using that ID so they can show the data in the template.

## Edit the `forecast.html` template
Now that we've got the data ready for our template, we can modify the HTML in our `app/views/forecast.html` file so it will display our forecast properly. The most dramatic change between this display and the display of our current weather data is that we have weather information for multiple days. This means we will need to loop through the results and display all of the weather information (similar to how we looped through the `citysearch` results previously).

Here is what the template should look like after you are done making edits:

```html

```