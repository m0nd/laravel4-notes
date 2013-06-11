Laravel 4 Notes
==================

Some notes I am making as I go along learning Laravel. 
Based on various sources like the [official docs](http://laravel.com/docs) and Dayle Reese's great [Code Happy tutorial](http://codehappy.daylerees.com/)

----------

## Contents ##
[Views](#views)   
  


## <a id="views"></a>Views ##

Views typically contain the HTML of your application and provide a convenient way of separating your controller and domain logic from your presentation logic. Views are stored in the app/views directory.

A simple view could look something like this (using no templating):

	<!-- View stored in app/views/greeting.php -->

	<html>
    	<body>
        	<h1>Hello, <?php echo $name; ?></h1>
    	</body>
	</html>

or like this (using the blade templating provided by Laravel):

	<!-- View stored in app/views/greeting.blade.php -->

	<html>
    	<body>
        	<h1>Hello, {{ $name; }}</h1>
    	</body>
	</html>

Notice the view using Blade templating has the extension `.blade.php` and it outputs variables simply using double curly braces `{{ $name }}` as opposed to regular php output `<?php echo $name; ?>`.

This view may be returned to the browser like so:

    Route::get('/', function()
    {
    	return View::make('greeting', array('name' => 'Taylor'));
    });

The second argument passed to `View::make` is an array of data that should be made available to the view.

###Methods of Passing Data To Views###

    // Pass an array of variableName => variableValue pairs
	// to make()
    $view = View::make('greeting', $data); 

or

    // Use with the "with" method which accepts a variable name
	// and value or an array of variable name/value pairs
    $view = View::make('greeting')->with('name', 'Steve');
    
 