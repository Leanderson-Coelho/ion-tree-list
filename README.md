# ion-tree-list [![Stories in Ready](https://badge.waffle.io/fer/ion-tree-list.png?label=ready&title=Ready)](https://waffle.io/fer/ion-tree-list)  [![devDependency Status](https://david-dm.org/fer/ion-tree-list/dev-status.svg?style=flat)](https://david-dm.org/fer/ion-tree-list#info=devDependencies) [![Bower version](https://badge.fury.io/bo/ion-tree-list.svg)](http://badge.fury.io/bo/ion-tree-list)

Ionic directive for displaying nested list ionic items.

Check [demo](http://fer.github.io/ion-tree-list/) link.

### Note:
#### I am actively looking for contributors who can port this library to [Ionic 2](http://ionic.io/2). If you are interested in doing so, don't hesitate to [drop me an email](mailto:fer+github@ferqwerty.com).

## Installation

```
bower install ion-tree-list --save
```

Add somewhere in your HEAD tag:

```
<script src="lib/ion-tree-list/ion-tree-list.js"></script>
```

Or fetch it from the [cdnjs](https://cdnjs.com/about) project : [https://cdnjs.com/libraries/ion-tree-list](https://cdnjs.com/libraries/ion-tree-list).

You'll need to add ```ion-tree-list``` as a dependency on your Ionic app:

```
angular.module('starter', [
    'ionic', 
    'controllers', 
    'services', 
    'ion-tree-list'
])
```

In your ```controller.js```:

```
  $scope.tasks = [
    {
      name: 'first task 1',
      tree: [
        {
          name: 'first task 1.1'
        }
      ]
    },
    {
      name: 'first task 2'
    }
  ];    
```


In your ```view.html```:

```
<ion-tree-list items="tasks" collapsed="true"></ion-tree-list>
```

Fetch clicked item by listening to ```$ionTreeList:ItemClicked``` in your controller:

## Emmited events

```
$scope.$on('$ionTreeList:ItemClicked', function(event, item) {
  // process 'item'
  console.log(item);
});

$scope.$on('$ionTreeList:LoadComplete', function(event, items) {
  // process 'items'
  console.log(items);
});
```

## Custom templates

Imagine your tasks in ```$scope.tasks``` in your ```controller.js``` has an extra attribute as ```checked```:

```
  $scope.tasks = [
    {
      name: 'first task 1',
      checked: false,
      tree: [
        {
          name: 'first task 1.1',
          checked: true
        },
      ]
    },
    {
      name: 'first task 2',
      checked: true
    }
  ];
```

In order to consume the ```checked``` value in your view, create a ```ion-item.tmpl.html``` file in 
your www folder containing the following:

```
<input type="checkbox" ng-model="item.checked"/>
{{item.name}}
```

Add an extra ```template-url``` attribute for your custom template:
 
```
<ion-tree-list items="tasks" template-url="'ion-item.tmpl.html'"></ion-tree-list>
```

## Contributing

Developers interested in contributing are very welcomed :)

Don't hesitate to ping me on my [email](mailto:fer@ferqwerty.com) if you are missing a feature, a fix or you simply want to contribute.

There's a list of issues right [here](https://github.com/fer/ion-tree-list/issues).
