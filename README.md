# docker-laravel-node

## node+laravel+nginxの基本のdockerファイルです
### cloneを実施
* Git Cloneをします。アプリを作成したいディレクトリ配下で以下のコマンドを実施します。  
    ```sh
    $ git clone https://github.com/matsuihiroki0221/docker-laravel-vue-base.git .
    ```

### フロント側アプリ作成
* フロントコンテナに入ります。
    ```sh
    $ docker-compose exec front bash
    ```

* frontコンテナに入ったら、Vue.jsもしくは、Reactアプリケーションを作成します 
    ```sh
    $ npm create vite@latest . -- --template vue-ts 
    // もしくは、
    $ npm create vite@latest . -- --template react-ts
    ```

* 作成されたアプリの`vite.config.js`を編集する  
dockr-composeをした際にアクセスされないため、hostに公開されるようにする
```
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

// https://vitejs.dev/config/
export default defineConfig({
  //ここを追加！
  server: {
    host: true
  },

  plugins: [vue()]
})
```

### バックエンド側アプリ作成
* api(php)コンテナに入る
```
$ docker-compose exec api bash
```

* composerを使用して、Laravelをインストールする。ヴァージョンは選択する事
```
composer create-project --prefer-dist "laravel/laravel=*.*" .
```
