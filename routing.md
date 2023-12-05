# Routing

What is routing? Routing is the process of taking a URI endpoint (that part of the URI which comes after the base URL) and decomposing it into parameters to determine which module, controller, and action of that controller should receive the request.

- Basic Routing
- Route defined in routes/web.php

  ```php
  Route::get('/', function () {
      return 'Hello World';
  });
  ```

- Route Controllers

  ```php
  Route::get('/user',[UserController::class, 'index']);
  ```

- Available Router Methods

  ```php
  Route::get($uri, $callback);
  Route::post($uri, $callback);
  Route::put($uri, $callback);
  Route::patch($uri, $callback);
  Route::delete($uri, $callback);
  Route::options($uri, $callback);
  ```

- We can also use the `match` method to match a URI to many HTTP verbs at once:

  ```php
  Route::match(['get', 'post'], '/', function () {
      //
  });
  ```

- Route Parameters

  ```php
  Route::get('user/{id}', function (string $id) {
      return 'User '.$id;
  });
  ```

- Optional Parameters
  ```php
  Route::get('user/{name?}', function (?string $name = null) {
      return $name;
  });
  ```
- Named Routes (! Route name should be unique)
  ```php
  Route::get('user/profile', function () {
      //
  })->name('profile');
  ```
- Generating URLs To Named Routes

  ```php
  $url = route('profile'); // http://localhost/user/profile
  ```

# [Next Step Controllers](controllers.md)
