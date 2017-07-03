# Views

Views in AngularJS are very powerful, but they can be a little confusing to wrap your mind around. When we talk about the "view", we are really talking about the rendered version of the template. When AngularJS templates are rendered, they are processed with all of the different components needed. That means the controllers, directives, services, and all of the other parts of your AngularJS app combine with the template to create the view.

When working with views, you will move between different components to adjust functionality. You may need to update the controller for a specific feature, or create a new directive to handle some custom formatting.

But in AngularJS views are orchestrated by the template. Templates bring together HTML, AngularJS directives, set up model relationships and much more. The behavior and presentation of a view can be radically altered by modifying the template, giving template developers a lot of strength in AngularJS apps.

Here is a simple example of an AngularJS template from angularjs.org:

```html
<html ng-app>
 <!-- Body tag augmented with ngController directive  -->
 <body ng-controller="MyController">
   <input ng-model="foo" value="bar">
   <!-- Button tag with ng-click directive, and
          string expression 'buttonText'
          wrapped in "{{ }}" markup -->
   <button ng-click="changeFoo()">{{buttonText}}</button>
   <script src="angular.js">
 </body>
</html>
```

Notice that it mostly looks like HTML except for the special attributes that start with `ng-` and the use of curly braces to output variable values \(`{{buttonText}}`\). The custom attributes are called "directives" in AngularJS lingo, and they represent complex Javascript functionality that can be accessed easily. For example, as a template writer all you have to do is use the `ng-model` directive to define the model for the input, but behind the scenes AngularJS is executing a complex set of code to attach the value of that input to a `$scope` variable and make that available to everything else in this view.

These are aspects of AngularJS templates that will become familiar as you work on building your webapp. As with HTML before it, there are lots of things to absorb, so the point is not to learn every single possible feature. Start with the few things you will use all the time, and then build out your knowledge from there.

