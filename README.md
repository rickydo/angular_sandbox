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