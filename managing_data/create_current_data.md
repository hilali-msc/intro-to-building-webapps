# Revisiting the `current` Data Resource
We built the current data resource in the previous chapter. In order to fit our current needs, we will want to alter the API URL we are using in one small way: We will switch from doing a text match on the name of the city to calling data for a specific city ID. We will use the ID returned from the `citysearch` service when we ultimately make this call.

## `current` resource
The `current` resource should be defined in the `app/scripts/services/current.js` file. That file should contain this resource definition:

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

This resource will still default to find results for the ID `'4717560'`, which is the ID for Paris, France. Note that the URL has been altered. Rather than sending the `q` parameter, we are sending the `id` parameter, and we are populating that parameter with the value of `cityID` in our `query()` method. When we use this in a controller, it will look something like this:

```js
$scope.currentWeather = current.query({
    cityID: 1234567
});
```

That code would set a `$scope` variable called `currentWeather` equal to the API response from OpenWeatherMap.org.

## Next Step: Create the view
In order to actually use this data in our app, we need to create a "current weather" view, which will involve creating a route that can take parameters. Let's do that now.