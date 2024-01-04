## Breeze のインストール

Breeze をインストールするには、次の Composer コマンドを実行してください:

```bash
composer require laravel/breeze:^1 --dev
```

## Inertia スタックの導入

Inertia スタックを使用するために Vue をインストールします:

```bash
php artisan breeze:install vue
```

その後、npm の依存関係をインストールし、セットアップを確認します:

```bash
npm install && npm run dev
```

Inertia のバージョン 1.0 に伴い、いくつかのライブラリの変更があります。`package.json`に次の 2 つのライブラリを追加し、`npm install`を実行します:

```json
"@inertiajs/inertia": "^0.11.0",
"@inertiajs/inertia-vue3": "^0.6.0"
```

`./resources/js/app.js`を更新します:

```javascript
import { createInertiaApp } from "@inertiajs/inertia-vue3";
```

## 仮想サーバの起動と動作確認

以下の 3 つのターミナルタブを開いてください:

1. フロントエンド開発:

```bash
npm run dev
```

2. バックエンド（アプリ）開発:

```bash
php artisan serve
```

3. 必要に応じてさまざまなコマンドを実行します。

## あると便利な拡張機能

-   Google Chrome: Vue.js devtools
-   Visual Studio Code: Volar

## Laravel Blade と Inertia の違い

### 1. サーバサイド

#### Laravel Blade

```php
view('viewファイル名', compact(変数名))
```

#### Inertia

```php
Inertia::render('コンポーネント名', [変数名])
```

### 2. クライアントサイド

#### Laravel Blade

```html
<a href="">リンク</a>
```

ページ内の情報をすべて再読み込みする HTML。

#### Inertia

```html
<link href="" />
```

JSON を部分的に読み込む。読み込むデータが少ないため、描画速度が速く、SPA に適しています。

## Link の確認

`routes/web.php`を更新:

```php
Route::get('/inertia-test', function() {
    return Inertia::render('InertiaTest');
});
```

次に、次のコマンドでルートを確認します:

```bash
php artisan route:list
```

`resources`ディレクトリにファイルを作成:

```bash
resources/js/Pages/InertiaTest.vue
```

```javascript
<script setup>
    import { Link } from '@inertiajs/inertia-vue3';
</script>

<template>
    Inertiaテストです。<br>
    <a href="/">aタグでWelcomeに移動</a><br>
    <Link href="/">LinkでWelcomeに移動</Link>
</template>

```

# 名前付きルート

ziggy ライブラリにより名前付きルートが使える

```vue
InertiaTest.vue
<Link :href="route('inertia.index')"></Link>

routes/web.php use App\Http\Controllers\InertiaTestController; ...
Route::get('/inertia/index', [InertiaTestController::class, 'index'])
->name('inertia.index');
```
