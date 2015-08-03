# File Changes in this Chapter
Here is a list of files that are altered in this chapter along with code examples showing what they should look like when you are finished. Reference these examples as you work to help you debug and evolve your code.

## `app/scripts/app.js`

```js
angular
  .module('yourApp', [
    'ngAnimate',
    'ngAria',
    'ngCookies',
    'ngMessages',
    'ngResource',
    'ngRoute',
    'ngSanitize',
    'ngStorage',
    'ngTouch'
  ])
  .config(function ($routeProvider) {
    $routeProvider
      .when('/', {
        templateUrl: 'views/main.html',
        controller: 'MainCtrl',
        controllerAs: 'main'
      })
      .when('/about', {
        templateUrl: 'views/about.html',
        controller: 'AboutCtrl',
        controllerAs: 'about'
      })
      .when('/current/:cityID', {
        templateUrl: 'views/current.html',
        controller: 'CurrentCtrl',
        controllerAs: 'current'
      })
      .when('/forecast/:cityID', {
        templateUrl: 'views/forecast.html',
        controller: 'ForecastCtrl',
        controllerAs: 'forecast'
      })
      .otherwise({
        redirectTo: '/'
      });
  });
```

## `app/scripts/services/citysearch.js`

```js
angular.module('yourApp')
  .factory('citysearch', function ($resource) {
    // Service logic
    // ...

    // Public API here
    return $resource('http://api.openweathermap.org/data/2.5/find?q=:query&units=imperial&type=like&mode=json&APPID=YOUR_API_KEY', {}, {
      find: {
        method: 'GET',
        params: {
          query: 'seattle'
        },
        isArray: false
      }
    });
  });

```

## `app/scripts/services/current.js`

```js
angular.module('yourApp')
  .factory('current', function ($resource) {
    // Service logic
    // ...

    // Public API here
    return $resource('http://api.openweathermap.org/data/2.5/weather?id=:cityID&units=imperial&APPID=YOUR_API_KEY', {}, {
      query: {
        method:'GET',
        params:{
          cityID: '4717560' // Paris, France ID
        },
        isArray:false
      }
    });
  });
```

## `app/scripts/services/forecast.js`

```js
angular.module('yourApp')
  .factory('forecast', function ($resource) {
    // Service logic
    // ...

    // Public API here
    return $resource('http://api.openweathermap.org/data/2.5/forecast/daily?id=:cityID&cnt=16&units=imperial&APPID=YOUR_API_KEY', {}, {
      query: {
        method:'GET',
        params:{
          cityID: '4717560' // Paris, France ID
        },
        isArray:false
      }
    });
  });

```

## `app/scripts/controllers/current.js`

```js
angular.module('yourApp')
  .controller('CurrentCtrl', function ($scope, $routeParams, current, $localStorage) {
    $scope.cityID = $routeParams.cityID;

    $scope.currentWeather = current.query({
        cityID: $routeParams.cityID
    });

    $scope.saveCity = function(city){
        var cityData = {
            'name': city.name,
            'id': city.id
        };
        if (!$localStorage.savedCities){
            $localStorage.savedCities = [cityData];
        } else {
            // Check to make sure we haven't already saved the city.
            var save = true;
            for (var i=0; i < $localStorage.savedCities.length; i++){
                if ($localStorage.savedCities[i].id == cityData.id) {
                    // this is a duplicate, so don't save
                    save = false;
                }
            }
            if (save==true){
                $localStorage.savedCities.push(cityData);
            } else {
                console.log('city already saved');
            }
        }
    };
  });
```

## `app/scripts/controllers/forecast.js`

```js
angular.module('yourApp')
  .controller('ForecastCtrl', function ($scope, $routeParams, forecast) {
    $scope.cityID = $routeParams.cityID;

    $scope.forecastData = forecast.query({
        cityID: $routeParams.cityID
    });
  });

```

## `app/scripts/controllers/main.js`

```js
angular.module('yourApp')
  .controller('MainCtrl', function ($scope, citysearch, $localStorage) {
    $scope.citiesFound = citysearch.find();
    $scope.storage = $localStorage;

    $scope.findCities = function(){
        $scope.citiesFound = citysearch.find({
            query: $scope.location
        });
        $scope.searchQuery = $scope.location;
    };
  });
```

## `app/views/current.html`

```html
<h1>Current Weather for {{currentWeather.name}}</h1>
<p><button class="btn btn-sm btn-primary" ng-click="saveCity(currentWeather)">Save City</button></p>
<dl>
    <dt>Currently</dt>
    <dd>{{currentWeather.weather[0].main}}</dd>
    <dd>{{currentWeather.weather[0].description}}</dd>
    <dt>Temperature</dt>
    <dd>{{currentWeather.main.temp}} &deg;F</dd>
    <dt>Wind</dt>
    <dd>{{currentWeather.wind.speed}} mph at {{currentWeather.wind.deg}} &deg;</dd>
    <dt>Clouds</dt>
    <dd>{{currentWeather.clouds.all}}%</dd>
</dl>

<p><a ng-href="/#/forecast/{{cityID}}" class="btn btn-lg btn-primary">View 16-day Forecast</a></p>
```

## `app/views/forecast.html`

```html
<h1>16-day Forecast for {{forecastData.city.name}} {{forecastData.city.country}}</h1>
<dl ng-repeat="weather in forecastData.list" class="weather-report">
    <dt>Forecast for {{weather.dt*1000 | date:'MMM dd, yyyy'}}</dt>
    <dd>{{weather.weather[0].main}}</dd>
    <dd>{{weather.weather[0].description}}</dd>
    <dt>Temperature</dt>
    <dd>Min: {{weather.temp.min}} &deg;F Max: {{weather.temp.max}} &deg;F</dd>
</dl>

<p><a ng-href="/#/current/{{cityID}}" class="btn btn-lg btn-primary">View Current Weather</a></p>
```

## `app/views/main.html`

```html
<div ng-app ng-controller="MainCtrl">
<div class="jumbotron">
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
<div ng-if="storage.savedCities">
  <h2>Saved Cities</h2>
  <ul class="saved-cities-list">
    <li ng-repeat="city in storage.savedCities">
      <a ng-href="/#/current/{{city.id}}" class="btn btn-lg btn-primary">{{city.name}}</a>
    </li>
  </ul>
</div>
</div>
```