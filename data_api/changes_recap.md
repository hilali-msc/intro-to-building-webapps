# Changes in this Chapter
Since this chapter involves several changes to several files, it can be tricky to make sure you've made all the required changes. Doublecheck your work against this page to make sure you didn't miss anything.

**Note: Every refrence to `yourApp` should be replaced with the name of your webapp.**

## `app/scripts/services/current.js`

```js
'use strict';

/**
 * @ngdoc service
 * @name yourApp.current
 * @description
 * # current
 * Factory in the yourApp.
 */
angular.module('yourApp')
  .factory('current', function ($resource) {
    // Service logic
    // ...

    // Public API here
    return $resource('http://api.openweathermap.org/data/2.5/weather?q=:location&units=imperial&APPID=d9947bfbe4d5f42fa39c0d5e08ff915f', {}, {
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

## `app/scripts/controllers/main.js`

```js
'use strict';

/**
 * @ngdoc function
 * @name yourApp.controller:MainCtrl
 * @description
 * # MainCtrl
 * Controller of the yourApp
 */
angular.module('yourApp')
  .controller('MainCtrl', function ($scope, current) {
    $scope.current = current.query();

    $scope.refreshCurrent = function(){
        $scope.current = current.query({
            location: $scope.location
        });
    };
  });

```

## `app/views/main.html`

```html
<div ng-app class="jumbotron" ng-controller="MainCtrl">
  <h1>Weather for {{current.name}}</h1>
  <p class="lead">
    <div ng-init="location='Seattle'">
        <p>
          <label for="location">Location:
            <input type="text" name="location" ng-model="location">
          </label>
        </p>
        <p>
          <button class="btn btn-lg btn-primary" ng-click="refreshCurrent()">Get Current Weather</button>
        </p>
      <dl>
        <dt>Currently</dt>
        <dd>{{current.weather[0].main}}</dd>
        <dd>{{current.weather[0].description}}</dd>
        <dt>Temperature</dt>
        <dd>{{current.main.temp}}</dd>
        <dt>Wind</dt>
        <dd>{{current.wind.speed}} mph at {{current.wind.deg}} degrees</dd>
        <dt>Clouds</dt>
        <dd>{{current.clouds.all}}%</dd>
      </dl>
    </div>
  </p>
</div>
```