# Find a City
In order to get a weather report, users must be able to find a city. As we mentioned, it's important to provide users a way to search and specify the exact city they want. We don't want to confuse Paris, France with Paris, Texas. So when a user searches for "Paris", we will show them both as options.

Once the user specifies which "Paris" they want to see weather for, we will use the "ID" for that city to make all of our calls to the OpenWeatherMap.org API. The ID is unique for each city, so if we make a call for data related to a specific city ID, then we know that we will get the correct information.

## Set up the `citysearch` model data resource
In order to perform the city search call, we will need to create a `citysearch` resource that we can use. To do this, we will follow the same basic steps as we followed to create the `current` resource we used in the last chapter.

First, run the Yeoman generator to generate the resource:

```
yo angular:factory citysearch
```
