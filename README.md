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