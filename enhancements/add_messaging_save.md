# Adding Messaging to City Saves
In order to provide a better user experience, we will add messaging to the "save city" button to indicate that the city has been successfully saved. In order to do that, we will need to make changes to the `app/views/current.html` template and the `app/scripts/controllers/current.js` file.

## How `ngMessages` works
[The `ngMessages` directive](https://docs.angularjs.org/api/ngMessages/directive/ngMessages) is a powerful tool for making different messages appear on the page. It allows you to define a set of messages in your template using HTML markup so you can style them and present them exactly as you wish. Then, in your controller, you only need to set up a Javascript object to trigger the messages.

This mechanism is supported by built in features of AngularJS, such as form validation that happens automatically based on HTML form configuration. But we can also use it however we want by setting up some simple message objects in our controllers.

We will step through the process of adding messages to the "save city" feature we created.

## Create an object to control our messages
In order to know whether or not to show a message, the `ngMessages` directive expects to receive an object it can parse that contains **boolean** values (true/false). We can create this object in the function where we save the city to localStorage.

Make the following changes to `CurrentCtrl` in the file `app/scripts/controllers/current.js`:

```js
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
            // Add object to trigger messages
            $scope.citySaved = {
                'success': true
            };
        } else {
            console.log('city already saved');
            // Add object to trigger messages
            $scope.citySaved = {
                'duplicate': true
            };
        }
    }
};
```

As you can see, the code above is for the `saveCity()` function, which expects to receive a `city` object and then saves that `city` into the `$localStorage.savedCities` array. We can easily define the `$scope.citySaved` object as part of this function. In the case where we save a new city, we set the `$scope.savedCity.success` value to `true`. In the case where the user has attempted to save a duplicate city, we set `$scope.savedCity.duplicate` to `true`.

These values will be interpreted by the `ng-messages` directive in our template so our messages can be shown at the proper time.

## Adding messages to the view template
Now that we have the `$scope.savedCity` value defined properly in our controller, we can add the following markup to the `app/views/current.html` template:

```html
<div ng-messages="citySaved">
    <p class="city-saved-alert bg-success text-success" ng-message="success">
        {{currentWeather.name}} has been saved to your list of cities.
    </p>
    <p class="city-saved-alert bg-warning text-warning" ng-message="duplicate">
        {{currentWeather.name}} has already been saved to your list of cities.
    </p>
</div>
```

The code above sets up our messages to be controlled by the `$scope.citySaved` object. First, we create a container `<div>` element, and we give it the `ng-messages` attribute. We set `ng-messages="citySaved"`, which tells the `ng-messages` directive to inspect the `$scope.citySaved` value in order to determine which messages below should be shown.

Within the `<div>` that contains our messages, we have defined `<p>` tags that possess the `ng-message` attribute. The first message, which is our "success" message, is triggered when `$scope.citySaved.success` is `true`. If that value is not `true`, then that message will not show.

Similarly, the second message is controlled by the value of `$scope.citySaved.duplicate`. If that value is `true`, then the message will be shown. If not, then it will be hidden.

Notice that the functionality of messages doesn't care about what classes, content, or HTML structures you have in your messages. Although the messages must be contained within an element that has the `ng-messages` attribute, you are otherwise free to create whatever HTML structure and assign whatever styles you wish. In this example, we are using default Bootstrap CSS styles to give the messages a "success" and "warning" look.

## Try it out
If you've successfully implemented these changes to the respective files, you should be able to test it out. Click into the current weather for a city and click the "save city" button. You should see one of these messages appear. Search, view and save a few cities to get an idea of how much this improves your app. Contemplate all the different things you could do with styling to improve the look and feel of these messages. Once again, there are many possibilities to explore here. Have fun and experiment.