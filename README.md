# graphql-api-sample

Docker環境で動作するGraphQL APIのサンプルです。

## 使用技術

- GraphQL
- TypeScript
- Node.js
- NestJS
- TypeORM
- MySQL

## 環境構築

**前提条件**
この環境を立ち上げるためにはDockerとmakeコマンドが必須です。

### ```cp .sample.env .env```を実行して、envファイルをコピーします

dbの名前や接続情報は好きな値を設定してください。

```
MYSQL_HOST=graphql_api_db
MYSQL_PORT=3306
MYSQL_DATABASE=
MYSQL_USER=
MYSQL_PASSWORD=
MYSQL_ROOT_PASSWORD=
```

### makeコマンドを実行して、Dockerイメージのビルドと、Dockerコンテナ内で```yarn install```を実行します

```sh
make setup
```

### Dockerコンテナを立ち上げます

```sh
docker-compose up -d
```

## マイグレーション

マイグレーションファイルが既にある場合は、Dockerコンテナの外で以下のコマンドを実行してください。


```
make migration:run
```

新しいテーブルを作成した場合は、エンティティを追加した後に、Dockerコンテナの外で以下のコマンドを実行するとマイグレーションファイルが実行されます。

**create-booksというマイグレーションファイルを作成**

```
make migration-generate name=create-books
```
