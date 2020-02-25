1 - Add following packages into your composer.json.

        "require": {
                        "infyomlabs/laravel-generator": "6.0.x-dev",
                        "laravelcollective/html": "^6.0",
                        "infyomlabs/adminlte-templates": "6.0.x-dev"
                    }  

2 - If you want to use Generate from Table option, you need to install.

        "require": {
                        "doctrine/dbal": "~2.3"
                    } 

3 - After adding packages, run the following command:

        composer update

4 - Add following alias to aliases array in config/app.php

        'Form'      => Collective\Html\FormFacade::class,
        'Html'      => Collective\Html\HtmlFacade::class,
        'Flash'     => Laracasts\Flash\Flash::class,

5 - Run the following command:

        php artisan vendor:publish

6 - Open app\Providers\RouteServiceProvider.php and update mapApiRoutes method as following:

        Route::prefix('api')
                    ->middleware('api')
                    ->as('api.')
                    ->namespace($this->namespace."\\API")
                    ->group(base_path('routes/api.php'));   

7 - Publish generator stuff:

        php artisan infyom:publish

8 - Generator also provides a quick way to publish layout and auth scaffold using the following command.

        php artisan infyom.publish:layout 

9 - Now, you have to enable menu option in config/infyom/laravel_generator.php. Make menu option true.

        'add_on' => [ 'menu' => [ 'enabled' => true ] ]
