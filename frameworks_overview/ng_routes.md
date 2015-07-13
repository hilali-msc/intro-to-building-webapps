# Routes
In any webapp, we face a challenge of locating different "screens" or "views" of our app. These are often equated to pages of the site, and in the case of webapps we often still want to retain the ability to link precisely to content within the app. This requires us to have URLs that make sense and can be used by the application to return users to specific screens or content. Much of web technology is built around having URLs that point to specific information, and web users tend to appreciate tools like their browser's back button. It's crucial that we do not break the way URLs function when we build webapps.

In AngularJS, there is a mechanism for providing `routes`, which allows us to, essentially, create "locations" within our webapp. The Javascript code to define routes might look something like this:

```js
phonecatApp.config(['$routeProvider',
  function($routeProvider) {
    $routeProvider.
      when('/phones', {
        templateUrl: 'partials/phone-list.html',
        controller: 'PhoneListCtrl'
      }).
      when('/phones/:phoneId', {
        templateUrl: 'partials/phone-detail.html',
        controller: 'PhoneDetailCtrl'
      }).
      otherwise({
        redirectTo: '/phones'
      });
  }]);
```
(Code sample borrowed from [angularjs.org documentation](https://docs.angularjs.org/tutorial/step_07).)

In this example, we can see that two different views are being configured: One view exists at `/phones` and will show a list of all phones in the system, controlled by the `PhoneListCtrl` controller. The other view exists at `/phones/:phoneId` and will show the information for just one phone model using the `PhoneDetailCtrl` controller. The `otherwise` clause tells the webapp that if the URL patterns do not match either of the two defined views, then route the user to the `/phones` view (the list of all the phones).