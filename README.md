# QrScanner

Este proyecto fue recopilado de http://tonyfreed.com/blog/ionic_barcode_scanner, a continuación lo explico.

Paso 1
Ejecutar el siguiente comando desde la consola de node.
ionic start IonicProject blank
cd IonicProject

Paso 2
Añadir plataformas
ionic platform add android
ionic platform add ios
Paso 3
Añadir plugin
cordova plugin add https://github.com/wildabeast/BarcodeScanner.git
bower install ngCordova
Paso 4
Referenciar a cordova
index.html
<script src="lib/ngCordova/dist/ng-cordova.js"></script>
app.js
angular.module('starter', ['ionic','ngCordova'])
Paso 5
añadir el controler del scanner
.controller('HomeCtrl', ['$scope','$cordovaBarcodeScanner','$ionicPlatform',
   function($scope,$cordovaBarcodeScanner,$ionicPlatform) {
      $scope.scan = function(){
         $ionicPlatform.ready(function() {
            $cordovaBarcodeScanner.scan().then(function(barcodeData) {
               alert(JSON.stringify(barcodeData));
            }, function(error) {
               alert(JSON.stringify(error));
            });
         });
      }
   }
])
Paso 6
Desde la vista llamar a la funcion anteriormente creada
<div style='background:red;display:table;margin:40% auto;padding:10px;color:white' ng-click='scan()'>
  Escanear código
</div>
