![img](images/logo-Transprent.png "laravel")

# LARAVEL-6-Developing-A-to-Z
All instructions for learning LARAVEL 5.7 for the beginner

## Installation Requirements:
- Composer (Must Installed)
- Xampp
- php v.7.2.0

## Installation Steps:

1. Goto your Xampp `htdocs` folder or open command promote in this folder.
2. type `composer create-project --prefer-dist laravel/laravel PROJECT_NAME_HERE` than press Enter.
3. After pressing enter laravel downloading process will be start in cmd.

![img](images/ins_1.png "laravel")

4. Open your browser type "localhost/PROJECT_NAME_HERE" and hit Enater.
5. Now show your Laravel Welcome Page in your browser.

## Configuration Routes:

1. Goto your project folder `routes/web.php`. web.php file store all path for route of our website.
2. This is the code for create new route
```
Route::get('/', function () {
    return view('welcome');
});
```
Here, `/` means `root` directory and the `function()` is anonymous function. Return carried a returning values for this path. `view()` function views the webpages that stored in `resources/views/` directory.

3. If we create a new routes `hello` that return a welcome text `Welcome User!`. So the code is
```
Route::get('/hello', function () {
    return "Welcome User!";
});
```
4. If we create another new routes `hello/abc` that return a welcome text as a veriable `Welcome`. So the code is
```
Route::get('/hello/abc', function () {
    $welcome = "Welcome User!";
    return $welcome;
});
```
It also passes all types of variables such as Array, String, Integer etc.
So, if we are passing a simple array data,
```
Route::get('/hello/abc', function () {
    $arry = array(21,6,'CAT', 'Dog', 'Cow');
    return $arry;
});
```

## Configuring Views:
1. Now we view the webpage from `resources/views/` directory.
2. Create a new webpage in `views` directory and page name `first_page.blade.php`. Here `blade` is the most powerful template engine.
3. create a new route in `routes/web.php` file,
```
Route::get('/first_page', function () {
    return view('first_page');
});
```
Here, `view()` is a function. View() called the webpage from `resources/views` directory.
4. Create another new webpage in `views/dir` directory.`dir` is the another inner directory of views directory. Now create webpage `second_page.blade.php` in `dir` directory.
5. create a new route in `routes/web.php` file,
```
Route::get('/second_page', function () {
    return view('dir.second_page');
});
```
Here, `dir.second_page` the dot(.) before `second_page` declare that the `dir` is folder or directory.
So, If we create more inner such as "inc", "OOP" directory than the code is,
```
Route::get('/second_page', function () {
    return view('dir.inc.oop.second_page');
});
```

## Create a Controller:
1. Goto project directory and open cmd type `php artisan make:controller Controller_name` than hit Enter.
2. Controller created in `app/http/controllers/` directory.
3. Open created controller `Controller_name` from `app/http/controllers/` directory.It's look like,
```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class first_controller extends Controller
{
    //
}

```
4. Now we create a public function `abc` in controller that returne a string `It's OK!`.
```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class controller_name extends Controller
{
    //
    public function abc(){

        return "It's OK!";
    }
}
```
5. Than create a new `controll` route in `routes/web.php` that access our controller function `abc`.
```
Route::get('/controll', 'controller_name@abc');
```
Here, `controller_name@abc` After @ text means method name and before @ text means controller name.

### Now we recive data and calculate in controller.
1. First create a reciveable route in `routes/web.php`. 
```
Route::get('/controll/{a}','Controller_name@abc');
```
Here, the `{a}` as a tempory variable for storing the reciving data. Or we called it is a reciving variable.
If we reciving a multiple data than we user multiple reciving variables.
```
Route::get('/controll/{a}/{b}/{c}','Controller_name@abc');
```
2. Now Configur controller for storing or calculation that reciving data.
3. Open `controller_name` controller and create public function `abc` with reciving variables.
```
class controller_name extends Controller
{
    //
    public function abc($x,$y,$z){

        echo $x.$y.$z;
    }
}
```
Here, $x,$y,$z are the sequentially reciving variables.
4. If you show webpage via controller just return the view function in method.
```
public function abc(){
  return view('dir.second_page');
}
```
5. If we send data into webpage than passing the value by view function. Now we are passing array type data into webpage.
```
public function abc($x){
  $aee = array(2,4,"cat",'dog');
  $value = $x;
  return view('dir.second_page', ['arr'=>$value, 'arry'=>$aee]);
}
```
6. Now recive the data from webpage. Goto your webpage file. just use dubble curly brackets{{ $arr }} and $arr variables name. For array printing code like below.
```
@foreach($arry as $data){
{{ data }}
}
@endforeach

//OR PHP
<?php
echo "<pre>";
  print_r($arry);
echo "</pre>;
?>
```

