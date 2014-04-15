##Introduction

This repository contains LiveTemplates for [AngularJS](http://angularjs.org/) and [Jasmine](https://github.com/pivotal/jasmine) to be used with [JetBrains](http://www.jetbrains.com/) products such as [IntelliJ](http://www.jetbrains.com/idea/) or [WebStorm](http://www.jetbrains.com/webstorm/).

Live Templates are a set of abbreviations that expand in to 'code snippets' for common tasks such as creating variables and functions. These abbreviations significantly speed up development and reduce coding errors.

Check out the [blog post](http://pkozlowskios.wordpress.com/2012/07/15/live-templates-for-angular-js-in-webstorm/) for more!

##Installation

### IntelliJ
Copy the Live Template xml files into your user's IntelliJ folder. This is typically in `[home directory]/.IntelliJIdea<version>/config/templates` or in `~/Library/Preferences/IntelliJIdea<version>/templates` on a Mac. If IntelliJ is currently open, you will need to restart the IDE.

Note: The default Live Template expansion character is TAB. To use a Live Template abbreviation, type the abbreviation and press the expansion character. The Live Template definitions can be found in the Settings Menu (CTRL+ALT+S), IDE Settings, Live Templates, angular.js.

### WebStorm
AFAIK WebStorm doesn't have any particular installation (or import) procedure for LiveTemplates.
Instead just drop `*.xml` files from this repository into WebStorm's folder where it stores LiveTemplates.
Usually this is the `[your home directory]/.WebIde40/config/templates`.

### Automatic with install-live-templates
If you are annoyed by a manual install, you should have a look at this useful project [install-live-templates](https://github.com/jamestalmage/install-live-templates)

1. Open terminal: get node & npm
2. Install via npm: `npm install -g live-template-installer`
3. Then go into this project on your side and run `live-templates install` or `live-templates backup`
4. You should restart WebStorm to import new templates!

*The file `./live_template_registry.json` lists all files which need to be installed or saved*

Please find more information about this package on his [github](https://github.com/jamestalmage/install-live-templates)!


##How to use the Live Templates
The following show the available abbrivations and their default implementations. Variables that are editable upon template expansion are delemited with the $ sign (ex. `$filterName$`).
`$END$` indicates where the cursor will be placed upon template completion.

##Live Templates
###AngularJS
####Globals
`ngc` - Define a new Angular Controller. You can change the controller name and parameters.

```JavaScript
var $controllerName$ = function($scope, $injectables$) {
    $END$
}
```
`ngfor` - angular.foreach loop

```JavaScript
angular.forEach($iterateOver$, function(value, key){
  $END$
});
```
####Scope related abbrevations
`$f` - Define a new $scope'd function (usually inside an AngularJS Controller). You can change the function name and arguments.

```JavaScript
$scope.$functionName$ = function($args$) {
    $END$
};
```
`$v` - Defines a new $scope'd variable inside an AngularJS controller.

```JavaScript
$scope.$variable$ = $value$;
$END$
```
`$va` - Defines a new $scope'd variable inside an AngularJS controller and assigns a value from a contstructor arguments.

```JavaScript
$scope.$variable$ = $variable$;
$END$
```
`$w` - Define a $watch for an expression. You can change the expression  to be watched.

```JavaScript
$scope.$watch('$watchExpr$',function(newValue, oldValue){
  $END$
});
```
`$on` - Define a $on for a $broadcast/$emit on the $scope inside an Angular Controller. You can change the event name to listen on.

```JavaScript
$scope.$on('$eventName$', function(event, $args$) {
    $END$
});
```
`$b` - Define a $broadcast for a $scope inside an Angular Controller / Angular Controller Function. You can change the event name and optional event arguments.

```JavaScript
$scope.$broadcast('$eventName$', $eventArgs$);
$END$
```
`$e` - Define an $emit for a $scope inside an Angular Controller / Angular Controller Function. You can change the event name and optional event arguments.

```JavaScript
$scope.$emit('$eventName$', $eventArgs$);
$END$
```
####Module related abbrevations
`ngm` - A new angular module without a config function.

```JavaScript
angular.module('$moduleName$',[$moduleDependencies$]);
$END$
```
`ngma` - A new angular module without a config function and a variable assigment.

```JavaScript
var $moduleName$ = angular.module('$moduleName$',[$moduleDeps$]);
$END$
```
`ngmc` - A new angular module with a config function

```JavaScript
var $moduleName$ = angular.module('$moduleName$',[$moduleDeps$], function($configDeps$){
    $END$
});
```
`ngmfa` - A factory in a module

```JavaScript
factory('$factoryName$', function($dependencies$){
  $END$
});
```
`ngms` - Define an Angular Module Service to be attached to a previously defined module. You can change the service name and service injectables.

```JavaScript
service('$serviceName$', function($injectables$) {
    $END$
});
```
`ngmfi` - Define an Angular Module Filter to be attached to a previously defined module. You can change the filter name.

```JavaScript
filter('$filterName$', function($injectables$) {
    return function(input, $args$) {
        $END$
    };
})
```
####Directives related abbrevations
`ngdcf` - A compile function

```JavaScript
function compile(tElement, tAttrs, transclude) {
      $END$
      return function (scope, element, attrs) {
      }
}
```
`ngdlf` - A linking function in a directive.

```JavaScript
function (scope, element, attrs$ctrl$) {
$END$
}
```
`ngdc` - A directive with a compile function

```JavaScript
directive('$directiveName$', function factory($injectables$) {
  var directiveDefinitionObject = {
    $directiveAttrs$
    compile: function compile(tElement, tAttrs, transclude) {
      $END$
      return function (scope, element, attrs) {
      }
    }
  };
  return directiveDefinitionObject;
})
```
`ngdl` - A directive with a linking function only.

```JavaScript
.directive('$directiveName$', function($directiveDeps$) {

    return function(scope, element, attrs$ctrl$) {
        $END$
    }
});
```
####Routes related abbrevations
`ngrw` - Defines a when condition of an AngularJS route.

```JavaScript
$routeProvider.when('$url$', {
    templateUrl: '$templateUrl$',
    controller: '$controller$'
});
$END$
```
`ngrwr` - Defines a when condition of an AngularJS route with the resolve block.

```JavaScript
$routeProvider.when('$url$', {
    templateUrl: '$templateUrl$',
    controller: '$controller$',
    resolve: {$END$
    }
});
```
`ngro` - Defines an otherwise condition of an AngularJS route.

```JavaScript
$routeProvider.otherwise(redirectTo : '$url$'});
$END$
```
####HTML - abbrevations to be used in HTML files
`ngindex` - Simple way of bootstraping angular app for prototyping purposes

```HTML
<html>
    <head>
        <script src="https://ajax.googleapis.com/ajax/libs/angularjs/$version$/angular.js"></script>
    </head>
    <body ng-app>
        $END$
    </body>
</html>
```
`ngsa` - Script tag importing base AngularJS file from CDN

```HTML
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/angularjs/$version$/angular$suffix$.js"></script>
$END$
```
`ngst` - A script tag holding Angular's template

```HTML
<script type="text/ng-template" id="$id$">
    $END$
</script>
```
`ngb` - A binding in AngularJS

```HTML
{{$binding$}}$END$
```
###Jasmine
####Various Jasmine + AngularJS abbrevations
`jasd` - Jasmine describe template

```HTML
describe('$describe$', function() {
    $END$
});
```
`jasi` - Jasmine it template

```HTML
it('$should$', function() {
    $END$
});
```
`jasbi` - beforeEach with Angular's inject

```HTML
beforeEach(inject(function(_$$rootScope_$other$){
  $END$
}));
```
`jasbm` - beforEach with AngularJS module

```HTML
beforeEach(module($moduleName$));
$END$
```
`jasb` - beforeEach

```HTML
beforeEach(function(){
  $END$
});
```
`jasii` - Jasmine it template with injectables

```HTML
it('$should$', inject(function($injectables$) {
    $END$
}));
```
`jasctrl` - Jasmine describe controller

```HTML
describe('$MyName$Ctrl', function() {
  var $rootScope,
      $scope,
      controller;
  beforeEach(function () {
    module('$module$', _dependencies_);

    inject(function ($injector) {
      $rootScope = $injector.get('$rootScope');
      $scope = $rootScope.$new();
      controller = $injector.get('$controller')('$MyName$Ctrl', {$scope. $scope});
    });

  });

  $END$

});
```
`jasdirective` - Jasmine describe directive

```HTML
describe('$MyName$', function() {
  var $rootScope,
      $scope,
      $compile,
      el,
      $body = $('body'),
      simpleHtml = '$directiveHtml$';

  beforeEach(function () {
    module('$module$', _dependencies_);

    inject(function ($injector) {
      $rootScope = $injector.get('$rootScope');
      $scope = $rootScope.$new();
      $compile = $injector.get('$compile');
      el = $compile(angular.element(simpleHtml))($scope);
    });

    $body.append(el);
    $rootScope.$digest();

  });

  $END$

});
```
`jasfactory` - Jasmine describe factory

```HTML
describe('$MyFactoryName$', function() {
  var factory;

  beforeEach(function () {
    module('$module$', _dependencies_);

    inject(function ($injector) {
      factory = $injector.get('$MyFactoryName$');
    });

  });

  $END$

});
```
`jasfilter` - Jasmine describe filter

```HTML
describe('$MyFilterName$', function() {
  var $filter, filter;

  beforeEach(function () {
    module('$module$', _dependencies_);

    inject(function ($injector) {
      $filter = $injector.get('$filter');
      filter = $filter('$MyFilterName$');
    });

  });

  $END$

});
```
####Jasmine expect and spyon shortcuts
`expectbe` - Expect(X).toBe(Y)

```HTML
expect($a$).toBe($b$);
$END$
```
`expectcloseto` - Expect(X).toBeCloseTo(Y, Z)

```HTML
expect($a$).toBeCloseTo($closeValue$, $precision$);
$END$
```
`expectcontain` - Expect(X).toContain(Y)

```HTML
expect($a$).toContain($b$);
$END$
```
`expectdefined` - Expect(X).toBeDefined()

```HTML
expect($a$).toBeDefined();
$END$
```
`expectequal` - Expect(X).toEqual(Y)

```HTML
expect($a$).toEqual($b$);
$END$
```
`expectfalse` - Expect(X).toBeFalsy(Y)

```HTML
expect($a$).toBeFalsy();
$END$
```
`expectgreaterthan` - Expect(X).toBeGreaterThan(Y)

```HTML
expect($a$).toBeGreaterThan($b$);
$END$
```
`expecthavebeencalled` - Expect(X).toHaveBeenCalled()

```HTML
expect($a$).toHaveBeenCalled();
$END$
```
`expecthavebeencalledwith` - Expect(X).toHaveBeenCalledWith(Y)

```HTML
expect($a$).toHaveBeenCalledWith($b$);
$END$
```
`expectlessthan` - Expect(X).toBeLessThan(Y)

```HTML
expect($a$).toBeLessThan($b$);
$END$
```
`expectmatch` - Expect(X).toMatch(Y)

```HTML
expect($a$).toMatch($b$);
$END$
```
`expectnotbe` - Expect(X).not.toBe(Y)

```HTML
expect($a$).not.toBe($b$);
$END$
```
`expectnotcontain` - Expect(X).not.toContain(Y)

```HTML
expect($a$).not.toContain($b$);
$END$
```
`expectnotedefined` - Jasmine expect().not.toBeDefined()

```HTML
expect($a$).not.toBeDefined();
$END$
```
`expectnotfalse` - Expect(X).not.toBeFalsy(Y)

```HTML
expect($a$).not.toBeFalsy();
$END$
```
`expectnotmatch` - Jasmine Expect(X).not.toMatch(Y)

```HTML
expect($a$).not.toMatch($b$);
$END$
```
`expectnotnukk` - Expect(X).not.toBeNull()

```HTML
expect($a$).not.toBeNull();
$END$
```
`expectnotthrow` - Expect(X).not.toThrow()

```HTML
expect($a$).not.toThrow();
$END$
```
`expectnottrue` - Expect(X).not.toBeTruthy(Y)

```HTML
expect($a$).not.toBeTruthy();
$END$
```
`expectnotundefined` - Expect(X).toBeUndefined()

```HTML
expect($a$).not.toBeUndefined();
$END$
```
`expectnull` - Expect(X).toBeNull()

```HTML
expect($a$).toBeNull();
$END$
```
`expectthrow` - Expect(X).toThrow()

```HTML
expect($a$).toThrow();
$END$
```
`expecttrue` - Expect(X).toBeTruthy(Y)

```HTML
expect($a$).toBeTruthy();
$END$
```
`expectundefined` - Expect(X).toBeUndefined()

```HTML
expect($a$).toBeUndefined();
$END$
```
`spyon` - spyOn(Obj, Key)

```HTML
spyOn($objToSpy$, '$objAttribute$')
$END$
```
`spyoncallfake` - spyOn(Obj, Key).andCallFake(fct)

```HTML
spyOn($objToSpy$, '$objAttribute$').andReturn($returnValue$)
$END$
```
`spyonreturn` - spyOn(Obj, Key).andReturn()

```HTML
spyOn($objToSpy$, '$objAttribute$').andReturn($returnValue$)
$END$
```
`spyonthrough` - spyOn(Obj, Key).andCallThrough()

```HTML
spyOn($objToSpy$, '$objAttribute$').andCallThrough()
$END$
```

##Credits
* [Pawel Kozlowski](https://github.com/pkozlowski-opensource) for initial creation of the Angular JS Live Templates
* [Jaymes Bearden](https://github.com/jaymes-bearden) expansion, testing and documentation
* [John Lindquist](https://github.com/johnlindquist) for showing what is possible with a good IDE in his amazing video tutorials