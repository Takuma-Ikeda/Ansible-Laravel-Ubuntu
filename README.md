# Ansible による Laravel 環境構築サンプル

Mac 環境から Ansible で Ubuntu 環境に下記ミドルウェアをインストール

- PHP 7.3.33
- MySQL 8.0.27
- Nginx

## 確認環境

- Ubuntu 21.10
  - https://github.com/Takuma-Ikeda/Linode-Terraform
  - 上記 Terraform で Linode に Ubuntu 環境をつくれます
- Laravel 8.75.0 のアプリをデプロイできました

# 手順

## README.md

- https://github.com/Takuma-Ikeda/Ansible-Laravel-Ubuntu-for-Mac/tree/main/ansible

## Laravel の作業

```sh
cp .env.example .env
vi .env
```

- `.env` を編集する

```
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=データベース
DB_USERNAME=ユーザ
DB_PASSWORD=パスワード
```

```sh
# php7.3 であることを確認
php -v

# PHP バージョンが違う場合、このコマンドで変更する
# update-alternatives --config php

composer install
php artisan key:gen
php artisan migrate --seed
npm i
npm run dev

# nginx 再起動
systemctl restart nginx
```
