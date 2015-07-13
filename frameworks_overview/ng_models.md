# Data Models
In AngularJS, Models represent the data that the system will work with. Models can be defined at almost any level of the application, and all sorts of components in the system can "watch" and react to models and changing data.

In this example from the AngularJS documentation, you can see how models are defined quickly using the `ng-model` attribute:

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

In this example, two inputs are put on the screen: one for "quantity", the other for "cost". As the user fills in this information, the total cost will be calculated and displayed.  