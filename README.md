# Breeze のインストール

[composer require laravel/breeze:^1 --dev]

# Inertia スタックを使用するための Vue のインストール

`php artisan breeze:install vue`

# npm のインストールと起動確認

`npm install && npm run dev`

Inertia ver1.0 に伴い、一部ライブラリの変更
package.json に下記二つのライブラリをついあして、'npm install'
`"@inertiajs/inertia": "^0.11.0",`
`"@inertiajs/inertia-vue3": "^0.6.0",`

./resources/js/app.js の一部変更
`'import { createInertiaApp } from '@inertiajs/inertia-vue3';'`

# 仮想サーバを立てて動作確認

ターミナルのタブを 3 つ開いておくとよい

1. フロント側
   `npm run dev`

2. バック（アプリ）側
   `php artisan serve`

3. 各種コマンド実行

# あると便利な拡張機能

GoogleChrome
Vue.js devtools

Visual Studio Code
Volar

# LaravelLBlade と Inertia の違い

1. サーバサイド
   Laravel Blade
   `view('viewファイル名', compact(変数名))`

Inertia
`Inertia::render('コンポーネント名', [変数名])`

2. クライアントサイド
   Laravel Blade
   `<a href="">リンク</a>`
   ページ内全ての情報を再読み込みする HTML

Inertia
`<Link href="">`
部分的に読み込む JSON
読み込む量が少ない = 描画速度が早い
SPA

# Link を確認してみる

`routes/web.php
Route::get('/inertia-test', function() {
    return Inertia::render('InertiaTest');
});`

ルートの確認は `php artisan route:list`

resources にファイル作成
`resources/js/Pages/InertiaTest.vue`
