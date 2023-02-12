# docker-laravel-node

## node+laravel+nginxの基本のdockerファイルです
* node環境については、使用するフレームワークに応じて、適宜変更してください
    * frontディレクトリにプロジェクトを用意してください
    * 使用するフレームワークに応じて、開発用と本番環境用にentrypointファイルを記載する事
* Laravelアプリ作成について
```
// api(php)コンテナに入る
$ docker-compose exec api bash

// composerを使用して、Laravelをインストールする。ヴァージョンは選択する事
composer create-project --prefer-dist "laravel/laravel=*.*" .

```