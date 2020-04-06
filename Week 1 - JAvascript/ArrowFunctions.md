# Arrow Functions

ES6 (ECMAScript 2015) arrow functions benefits:

1. Shorter syntax
2. The value of **_this_** follows its **lexical scope**

![this](https://pics.me.me/arrow-functions-this-isthis-this-imgflip-com-es6-arrow-functions-60868023.png "this")

The real value in arrow functions is not in the syntax reduction but in the way it manages **"this"** for you.

## Lexical Scoping

It's a fancy way of saying **"this"** comes from the surrounding scope where the function is called. Traditionally, functions in JavaScript bind their own **"this"** value, however in an arrow function, its value is fetched lexically from the scope it sits within. It (the arrow function itself) has no **"this"**, so it assumes the outer scope when **"this"** is called within an arrow function.

```
function Grab (FoodService) {
  this.driver = 'Hello';
  FoodService
  .doSomething(function (response) {
    this.driver = response; //undefined or unexpected value
  });
}
```

In traditional functions, **_this.driver = response_** won't work as intended because it's been executed in a different context.

You can call .bind like:

```
function Grab (FoodService) {
  this.driver = 'Hello';
  FoodService
  .doSomething(function (response) {
    this.driver = response;
  }.bind(this)); //binding
}
```

or keep a top-level reference e.g. **_that = this_** to get the right **_this_**:

```
function Grab (FoodService) {
  let that = this; //top level reference
  that.driver = 'Hello';
  FoodService
  .doSomething(function (response) {
    that.driver = response;
  });
}
```

With arrow functions, we can rewrite the above code into:

```
function Grab (FoodService) {
  this.driver = 'Hello';
  FoodService
  .doSomething(response => this.driver = response);
}
```

The scope is inherited automatically and the value of **_this_** would be bound correctly.

You get to save yourself from having to .bind, .call, .apply and having to write that=this.
