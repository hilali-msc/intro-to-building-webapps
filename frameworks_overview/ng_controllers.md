# Controllers
In AngularJS, Controllers are the primary Javascript code that determines how some specific component or View functions. In view templates, we define which controllers affect which components on the page. It's possible to have a controller entirely dedicated, for example, to a "favorite" button. Or, we might have a controller attached to the template as a whole (such as the `PhoneListCtrl` in the previous example).

Controllers handle the logic that makes the view function and they make data available to the templates by defining the `$scope` variable. In AngularJS, each Controller has a `$scope`, which is a data object used to contain all of the information available to the template. In a template, using the `ng-model` attribute to define a new model is actually the same as defining that model in the `$scope` object in the Controller for that View.

This in-template `ng-model` definition:

```html
<input type="text" ng-model="username">
```

is actually creating this value:

```js
$scope.username
```

If we were to initialize the value in the Controller for this example View, then we would write something like this:

```js
$scope.username = "Initial Value"
```

And that would cause the input to be populated with the name "Initial Value" when the View first loads.

In the Controller for our view, we can define the different functions that could be carried out. Look at the example we saw previously for calculating total cost:

```html
<div ng-app ng-init="qty=1;cost=2">
  <b>Invoice:</b>
  <div>
    Quantity: <input type="number" min="0" ng-model="qty">
  </div>
  <div>
    Costs: <input type="number" min="0" ng-model="cost">
  </div>
  <div>
    <b>Total:</b> {{qty * cost | currency}}
  </div>
</div>
```

That same functionality could be rewritten like this. First, in the template:

```html
<div ng-app ng-init="qty=1;cost=2">
  <b>Invoice:</b>
  <div>
    Quantity: <input type="number" min="0" ng-model="qty" ng-change="calculateCost()">
  </div>
  <div>
    Costs: <input type="number" min="0" ng-model="cost" ng-change="calculateCost()">
  </div>
  <div>
    <b>Total:</b> {{totalCost | currency}}
  </div>
</div>
```

And then in the Javascript controller:

```js
$scope.calculateCost = function() {
    $scope.totalCost = $scope.qty * $scope.cost;
};
```