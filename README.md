# PHP/Nginx/MySql環境を、Dockerで構築

PHPをちょっと触ってみたい人向け、
いちいちapacheとかインストールして設定するのが面倒だったので、
Docker環境で作ってみました。

### 環境
- macOS Catalina
- docker compose
- php 8.0.18
- nginx 1.21.6 
- mysql 8.0.29
- Sequel Ace(MySQLのGUI)

### ディレクトリ構造
```
mysql
  ├── data
  ├── my.cnf
nginx
  ├── conf.d
  ├──── default.conf
  ├── html(このhtmlフォルダ以下のファイルがブラウザで開けるようになる)
php 
  ├── Dockerfile
  ├── php.ini
.env_mysql(DB接続情報はここに入れる)
docker-compose.yml
```

### クローン
```
git clone git@github.com:yozakurakirei/php-nginx-mysql.git
```

### .env_mysqlファイル作成
```
touch .env_mysql

// 作成した.envファイルに下記のようにDB情報を追記
MYSQL_DATABASE=データベース名
MYSQL_USER=ユーザー名
MYSQL_PASSWORD=パスワード
MYSQL_ROOT_PASSWORD=パスワード
```

### ビルド、コンテナ起動
```
docker-compose up --build -d
```

### ブラウザ上からmysqlに接続できているか確認
```
nginx/html/index.php
const HOSTNAME = 'mysql';
const DATABASE = 'データベース名';
const USERNAME = 'ユーザー名';
const PASSWORD = 'パスワード';
```

接続できたら、見やすいようにSequelAceなどとも接続すればOK😷

以上になります。
あとは、ご自由にカスタムしていただければと思います。
