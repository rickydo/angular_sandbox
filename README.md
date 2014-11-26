angular_sandbox
===============

Angular notes for myself:

ng-app is directive that creates an angular application by running the corresponding module 'store' in js. 

this will run the html inside the element as part of the angular app

Expressions:
Allow you to insert dynamic values into your html

Controllers:
where we define our app's behavior by defining functions and values.
Wrapping your JS in a closure is a good habit
ng-controller
"StoreController as store" where store is the alias

ng-show="store.product.canPurchase" will only show the element if the values of the expression is true.

ng-repeat = the equivalent of iterating over an array

Filters:
{{ data| filter:options}}
date:
{{'13881234123123' | date: "MM/dd/yyyy @ h:mma"}} 12/27/2013 @ 12:50AM
uppercase and lowercase:
{{'octagon gem' | uppercase}} OCTAGON GEM
| currency => gives the price with decimal places

limitTo
{{'My Description' | limitTo:8}} My Descr
<li ng-repeat="product in store.products | limitTo:3">

orderBy:
<li ng-repeat="product in store.products | orderBy: '-price'">
will list the prices in desc order

to link images 
<img ng-src="{{product.images[0].full}}"/>

for making tabs
<a href ng-click="tab = 1"> Tab name</a>

When ng-click changes the values of tab, the {{tab}} expression automatically gets updated

Expressions define a 2-way Data Binding, this means expressions are re-evaluated when a property changes

ng-class ="{active:tab === n}"
this sets a class active if the expression on the right evaluates to true

ng-model binds the form element value to the property
	ng-model can have type="checkbox" or type="radio"

to clear out a previous review you can add a line to create a new object which will reset

ng-submit allows actual submission of input

novalidate-to turn off default html validation

required-to mark required fields

$valid-$ is referencing a property on the form. valid is a built in property in angular

source before typing email
class="ng-pristine ng-invalid"

source with invalid email
class="ng-dirty ng-invalid"

source with valid email
class="ng-dirty ng-valid"

angular has built-in validations for common input types
email, url, number (can define min and max)

to eliminate duplication in templates use ng-include
ng-include is expecting a variable with the name of the file to include. to pass the name as 
a string, use single quotes 

Why write directives?
Directives allow you to write HTML that expresses the behavior of your application

Template-expanding directives:
	define a custom tag or attribute that is expanded or replaced
	can include controller logic 

directives can also be used for expressing complex UI, calling events and registering event handlers, reusing common components

How to build custom directives
	dash in HTML translates to camelCase in JS

first we have to define the directive in the js file
	app.directive('productTitle', function(){
	return {
		a configuration object defining how your directive will work
			restrict: 'E',						# 'E' for Element
			templateUrl: 'product-title.html'	#Url of a template
		};
	})	

Element Directive: use element directives for UI widgets 
<product-title></product-title>

Attribute Directive: use Attribute Directives for mixin behaviors like a tooltip
<h3 product-title></h3>
restrict: 'A' #for attribute

separate dependencies into separate files

Services: give your Controller additional functionality like..
-fetching JSON data from a web service with $http
--the $http service is how we make an async request to a server
---by using $http as a function with an options object
----$http({method: 'GET', url: '/products.json'});
---or using one of the shortcut methods
----$http.get('/products.json', {apiKey: 'myApiKey'})
---both return a Promise object with .success() and .error()
---if we tell $http to fetch JSON, the result will be automatically decoded into Javascript objects and arrays
-logging messages to the Javascript console with $log
-filtering an array with $filter

Injecting dependencies:
app.controller('SomeController', ['$http', function($http){
	this.products = ???;
}])





















	