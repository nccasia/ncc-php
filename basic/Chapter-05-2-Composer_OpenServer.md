# OpenServer
- OpenServer is a software for creating webserver on windows from Russia, and there are many good utilities built in.
- OpenServer provides users with a variety of platforms to test their products and run well in all environments.
- OpenServer has built-in environment variables within it when working with Laravel.

- Download và install OpenServer
    - Step 1: Access the [link download](https://ospanel.io/) and select an installation file and corresponding configuration file to download and install.
    - Step 2: Once downloaded we will have a file with the name Open_server _ ***. Exe, run the file to begin the installation.
    - Step 3: Configure and use OpenServer.
    - To make it easier to visualize the installation process, you go to [Link cài đặt](https://freetuts.net/cai-dat-openserver-va-tao-domain-ao-tren-localhost-281.html)

# Composer
_Composer là 1 dependency manager, dùng để cài đặt và quản lý các package, library dùng cho dự án PHP.<br>
_Composer hoạt động dựa vào file composer.json, file khai báo và cấu hình các package theo cấu trúc json.<br>
_Sau khi cài đặt, thông tin về package sẽ được lưu trong file composer.lock (do composer tự sinh ra). Nếu khi cài đặt mới mà trong project có file lock, composer sẽ cài đặt theo thông tin có trong file này.<br>
_Các package sau khi cài sẽ nằm trong thư mục vendor.<br>
_Lợi ích của composer:<br>
Giúp tinh gọn hơn project dự án vì không cần phải tích hợp sẵn các thư viện ngoài.<br>
Ngoài ra nếu trong thư viện cần phải cài một thư viện khác nữa thì composer cũng tự động cài đặt luôn, rất tiện lợi cho nhà phát triển.<br>
Composer cũng hỗ trợ tốt cả MacOS, Window và Linux.

Example
```json
{
	"name" : "my project",
	"type" : "project",
	"description" : "My project",
	"keywords" : [
		"framework",
		"laravel"
	],
	"license" : "MIT",
	"require" : {
		"php": "^8.0",
		"twilio/sdk": "^6.15"
	},
	"require-dev" : {
		"barryvdh/laravel-ide-helper": "^2.8",
		"phpunit/phpunit": "9.5"
	},
	"config" : {
		"optimize-autoloader" : true,
		"preferred-install" : "dist",
		"sort-packages" : true
	},
	"extra" : {},
	"autoload" : {
		"psr-4" : {
			"App\\" : "app/",
			"Database\\" : "Database/"
		},
		"classmap" : [
			"database/seeds",
		]
	},
	"autoload-dev" : {
		"psr-4" : {
			"Tests\\" : "tests/"
		}
	},
	"minimum-stability" : "dev",
	"prefer-stable" : true,
	"scripts" : {
		"post-autoload-dump" : [
			"Illuminate\\Foundation\\ComposerScripts::postAutoloadDump",
			"@php artisan package:discover --ansi"
		],
		"post-root-package-install" : "@php -r \"file_exists('.env') || copy('.env.example', '.env');\"",
		"post-create-project-cmd" : "@php artisan key:generate --ansi"
	}
}
```
Như trên ta sẽ có thư viện twilio phiên bản 6.15

_Cài đặt bằng lệnh:

    - composer install


