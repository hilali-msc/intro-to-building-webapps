# Find a City
In order to get a weather report, users must be able to find a city. As we mentioned, it's important to provide users a way to search and specify the exact city they want. We don't want to confuse Paris, France with Paris, Texas. So when a user searches for "Paris", we will show them both as options.

Once the user specifies which "Paris" they want to see weather for, we will use the "ID" for that city to make all of our calls to the OpenWeatherMap.org API. The ID is unique for each city, so if we make a call for data related to a specific city ID, then we know that we will get the correct information.

## Set up the `citysearch` model data resource
In order to perform the city search call, we will need to create a `citysearch` resource that we can use. To do this, we will follow the same basic steps as we followed to create the `current` resource we used in the last chapter.

First, run the Yeoman generator to generate the resource:

```
yo angular:factory citysearch
```

That command, as it did previously, will create a new file in `app/scripts/services/` called `citysearch.js`. Inside that file, you will find the stub of a resource. You will want to modify that stub to use the `$resource` object and add in the OpenWeatherMap.org API URL pattern. This will follow the same pattern as we used in the previous chapter. The proper URL to perform a city search using the OWM Find API should look like this:

```html
http://api.openweathermap.org/data/2.5/find?q=paris&type=like&mode=json&APPID=YOUR_APP_ID_HERE
```

Once we are done creating the resource definition, it should look like this:

```js
angular.module('yourApp')
  .factory('citysearch', function ($resource) {
    // Service logic
    // ...

    // Public API here
    return $resource('http://api.openweathermap.org/data/2.5/find?q=:query&type=like&mode=json&APPID=YOUR_APP_ID', {}, {
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

Looking at the code we've generated, you can see that we have mostly recreated the same setup as in the `current` resource (defined in `app/scripts/services/current.js`). You can identify that we have replaced the string `paris` in our example with the template placeholder `:query` and we supply a default value of `'seattle'` if no other value is specified. That means our app will, by default, return `citysearch` results for "seattle", but we can alter that whenever we make the search call. 

Also note that we are defining a `find()` method here. So when we access this data, we will use code that looks like this:

```js
$scope.citiesFound = citysearch.find({
    query: $scope.searchText
});
```

