# AngularJS-Weather-Application

First register with https://openweathermap.org/api. you will get a URl like this 'http://api.openweathermap.org/data/2.5/forecast/daily' with apicode. This url provides the weather api data in JSON format. the you can access it using angularjs easily.

app.js

    var app = angular.module('jsbin', []);

    app.controller('DemoCtrl', function($http,$scope) {
  
      var vm = this;

      var URL = 'http://api.openweathermap.org/data/2.5/forecast/daily';

      var request = {
        method: 'GET',
        url: URL,
        params: {
           q: 'London,uk',
           mode: 'json',
           units: 'metric',
           cnt: '7',
          appid: '2206d84c8189efe365465e3318f487aa'
        }
      };


      $http(request)
        .then(function(response) {
          vm.data = response.data;
        vm.city = response.data.city.name;
        vm.country = response.data.city.country;
        vm.lat = response.data.city.coord.lat;
        vm.lon = response.data.city.coord.lon;
        console.log(vm.data);
        }).
        catch(function(response) {
          vm.data = response.data;
        });



    });
