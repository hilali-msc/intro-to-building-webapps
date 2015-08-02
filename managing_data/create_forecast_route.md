# Creating the `forecast` Route and View
Creating the forecast view is almost identical to creating the current weather view. The two start with the same basic Yeoman command:

```bash
yo angular:route forecast
```

Once you've run that command you should be able to see the controller file (`app/scripts/controllers/forecast.js`), view template (`app/views/forecast.html`) and the changes inside of `app/scripts/app.js`:

```js
.when('/forecast', {
    templateUrl: 'views/forecast.html',
    controller: 'ForecastCtrl',
    controllerAs: 'forecast'
})
```

Once again, we will modify that route definition so it will accept a route parameter called `cityID`:

```js
.when('/forecast/:cityID', {
    templateUrl: 'views/forecast.html',
    controller: 'ForecastCtrl',
    controllerAs: 'forecast'
})
```