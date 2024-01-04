# Breeze のインストール

[composer require laravel/breeze:^1 --dev]

# Inertia スタックを使用するための Vue のインストール

[php artisan breeze:install vue]

# npm のインストールと起動確認

[npm install && npm run dev]

Inertia ver1.0 に伴い、一部ライブラリの変更
package.json に下記二つのライブラリをついあして、'npm install'
"@inertiajs/inertia": "^0.11.0",
"@inertiajs/inertia-vue3": "^0.6.0",
