# Files Changed in This Chapter
In order to implement the changes described in this chapter, the following files have been altered. They are quoted below so you can compare your work to a full view of the file.

## `app/views/current.html`

```html
<h1>Current Weather for {{currentWeather.name}}</h1>
<p ng-if="!citySaved"><button class="btn btn-sm btn-primary" ng-click="saveCity(currentWeather)">Save City</button></p>
<div ng-messages="citySaved">
    <p class="city-saved-alert bg-success text-success" ng-message="success">
        {{currentWeather.name}} has been saved to your list of cities.
    </p>
    <p class="city-saved-alert bg-warning text-warning" ng-message="duplicate">
        {{currentWeather.name}} has already been saved to your list of cities.
    </p>
</div>
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

## `app/scripts/current.js`

```js
angular.module('weatherApp')
  .controller('CurrentCtrl', function ($scope, $routeParams, CurrentWeather, $localStorage) {
    $scope.cityID = $routeParams.cityID;

    $scope.currentWeather = CurrentWeather.query({
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
                if ($localStorage.savedCities[i].id === cityData.id) {
                    // this is a duplicate, so don't save
                    save = false;
                }
            }
            if (save===true){
                $localStorage.savedCities.push(cityData);
                $scope.citySaved = {
                    'success': true
                };
            } else {
                console.log('city already saved');
                $scope.citySaved = {
                    'duplicate': true
                };
            }
        }
    };
  });

```

## `app/styles/main.scss`

```css
$icon-font-path: "../bower_components/bootstrap-sass-official/assets/fonts/bootstrap/";
@import "variables"; // Override default Bootstrap values.
// bower:scss
@import "bootstrap-sass-official/assets/stylesheets/_bootstrap.scss";
// endbower

@import "content";
@import "buttons";
@import "transitions";
```
## `app/styles/_transitions.scss`

```css
// Styles for animated transitions of HTML elements
div[ng-view].ng-enter {
    -webkit-animation: fadeIn 0.5s;
    animation: fadeIn 0.5s;
}
div[ng-view].ng-leave {
    -webkit-animation: fadeOut 0.5s;
    animation: fadeOut 0.5s;
}
```
