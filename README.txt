# LaravelRESTfulAPI

1. Install laravel project
composer create-project laravel/laravel:^8.0
2. Install passport package
composer require laravel/passport
3. Run migrate
php artisan migrate
-> Fix error:  SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long; max key length is 1000 bytes (SQL: alter table `users` add unique `users_email_unique(`email`))
-> D:\LaravelRESTfulAPI-PassportAuth\app\Providers\AppServiceProvider.php
->use Illuminate\Support\Facades\Schema;
->Schema::defaultStringLength(191);
4. Install passport
php artisan passport:install
Sẽ tạo ra dữ liệu cho 2 bảng này: oauth_clients, oauth_personal_access_clients
5. Edit file model user
->use Laravel\Passport\HasApiTokens;
->use HasApiTokens, HasFactory, Notifiable;
6. Edit file config/auth.php
-> 'api' => [
            'driver' => 'passport',
            'provider' => 'users',
        ],
7. Add product table and model
-> php artisan make:migration create_products_table
-> php artisan make:model Product
8. Edit code trong model product vừa tạo
$table->id();
$table->string('name');
$table->text('detail');
$table->timestamps();
7. Run migrate
->php artisan migrate
8. Create api route
->routes/api.php
9. Create Controller Files
->php artisan make:controller API/BaseController
->php artisan make:controller API/RegisterController
->php artisan make:controller API/ProductController
10. Create Eloquent API Resources
->php artisan make:resource Product
11. Insert các function cho BaseController
12. EDIT Các controller còn lại sẽ extends tới BaseController nhé
