# Create the `forecast` data resource
In order to use the [16-day Forecast API](http://openweathermap.org/forecast16) from OpenWeatherMap.org, we will once again create a new factory service using the Yeoman generator:

```ssh
yo angular:factory forecast
```

Once we have that, inside of `app/scripts/services/forecast.js` we will create the following resource definition:

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

As always, you will need to substitute in your own API key and the name of your AngularJS app, but otherwise you should have something similar in your own code. Once you have the basics of working with a particular API settled, it should become trivial to create these resources.