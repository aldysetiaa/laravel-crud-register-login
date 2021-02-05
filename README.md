Cara install project laravel
1. Download project
2. ``` install composer ``` pada direktori project
- apabila ada kendala (error) 
```Script @php artisan package:discover handling the post-autoload-dump event returned with error code 1 
In PackageManifest.php line 122:
Undefined index: name
```

edit file composer.json
bagian  
```
"extra": {
        "laravel": {
            "dont-discover": [ 
            ]
        }
    },

menjadi


"extra": {
        "laravel": {
            "dont-discover": [
              "laravel/dusk"
            ]
        }
    },
```


lakukan langkah berikutnya


3. (composer update) pada cmd, tunggu hingga proses selesai

4. ``` php artisan migrate ``` untuk database baru dan kosong, jangan lupa dbuat terlebih dulu database nya di phpmyadmin dan edit file database.php di folder config bagian mysql sesuaikan dngan setingan di komputer anda
```
    'mysql' => [
            'driver' => 'mysql',
            'host' => env('DB_HOST', 'localhost'),
            'port' => env('DB_PORT', '3306'),
            'database' => env('DB_DATABASE', 'ubadi'),
            'username' => env('DB_USERNAME', 'root'),
            'password' => env('DB_PASSWORD', ''),
            'unix_socket' => env('DB_SOCKET', ''),
            'charset' => 'utf8mb4',
            'collation' => 'utf8mb4_unicode_ci',
            'prefix' => '',
            'strict' => true,
            'engine' => null,
        ],
```

5. setelah selesai, aktifkan server dengan : ``` php artisan serve ```
note jika serve aktif namun di browser 127.0.0.1:8000 ``` error 500 Whoops, something went wrong on our servers ```

lakukan cara ini :

1. duplicate .env.example dan rename menjadi .env
2. ketik di cmd  php artisan key:generate sampai info successfully
3. ``` php artisan serve ```
lalu server aktif dan akses kembali 127.0.0.1:8000

catatan : jika error ```homestead using password yes ```, modifikasi file .env bagian database user dan password dan sesuaikan dengan setingan server
