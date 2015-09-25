# Routeador Simple, Basic and Easy PHP Routing Made By Anthony Gonzalez

Uses the [Altorouter](http://altorouter.com/) as foundation.

# Usage

It will match a url path and called a class method dynamically:

If project in subfolder set base path:
```php
Route::set_base_path('/routeador');
```

Root path, example below it will call the method UsersController::index():
```php
Route::root_to('users#index');
```

Route resourceful routes, the example below it will match the next 8 routes:
Method           Path                    Action
GET              /users                  index
GET              /users/new              new_user
POST             /users                  create
GET              /users/[i:id]           show
GET              /users/[i:id]/edit      edit
PATCH|POST       /users/[i:id]           update
POST             /users/[i:id]/delete    delete
DELETE           /users/[i:id]           destroy
```php
Route::resources('users');
```
If only specific resources are needed pass an associative array with the key only and array as value with specified actions:
```php
Route::resources( 'users', array( 'only' => array('create', 'new_user', 'show') ) );
```
If specific resources are not needed:
```php
Route::resources( 'users', array( 'except' => array('create', 'new_user', 'show') ) );
```

To match the routes and call class methods actions, it needs to be called after all routes are added:
```php
Route::call_target_method(Route::submit());
```

To add a route:
```php
Route::add($method, $path, $action, $name);
```

To submit and match routes(remember to call this function after all routes are added):
```php
Route::submit();
```

To add multiple routes as one as multidimensional array:
```php
Route::add_routes($array);
```

To generate path from matched routes:
```php
Route::generate_path($route_name, $params);
```

To get routes list:
```php
Route::get_routes();
```

To add specific match type:
```php
Route::add_match_type($match_types);
```