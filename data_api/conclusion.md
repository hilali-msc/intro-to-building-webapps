# Data Conclusion
This ends our first foray into getting data inside of our app. Using a third party data API, we have successfully wired up a factory service that makes a data resource available to use throughout our application. Any controller that needs to leverage the current weather forcast may make use of the `current` service and will be able to easily query for weather data.

In order to achieve this, we have used `ngResource`, `$resource`, and OpenWeatherMaps.org. We now have a pattern established that can be followed to create additional resources, or to use this resource more in our webapp. Each resource contains its own configuration, methods, and API endpoints. You can leverage multiple API services inside a single app by creating separate resources for each one.

All of these possibilities are opened up with the simple architecture we've laid out here. AngularJS helps us keep our views updated, and makes it much easier to access our third party data APIs. 

Now that we have data, we need to effectively make use of it. We have a "proof of concept" in place, and a pattern we can use to finish out our work, but we are not yet done. In the next chapter we will explore how to manage and work with data in ways that are useful to our users.