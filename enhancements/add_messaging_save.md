# Adding Messaging to City Saves
In order to provide a better user experience, we will add messaging to the "save city" button to indicate that the city has been successfully saved. In order to do that, we will need to make changes to the `app/views/current.html` template and the `app/scripts/controllers/current.js` file.

## How `ngMessages` works
[The `ngMessages` directive](https://docs.angularjs.org/api/ngMessages/directive/ngMessages) is a powerful tool for making different messages appear on the page. It allows you to define a set of messages in your template using HTML markup so you can style them and present them exactly as you wish. Then, in your controller, you only need to set up a Javascript object to trigger the messages.