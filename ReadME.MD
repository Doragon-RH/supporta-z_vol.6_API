# hackathon_vol.6_api

## こちらはTODOアプリのバックエンド部分となります。
## 共同開発者：shirasu-48
## 担当部分：Doragon-RH：DB連携、やること、やったことを取得、追加、変更、削除するAPI作成
## shirasu-48：chatGPTのレスポンスを返すAPI作成、フロントエンドからアクセスできるように、HTTPメソッドの使用許可設定
## フロント部分は、https://github.com/nepp-tumsat/hackathon_vol.6 を参照してください。
## ChatGPTのAPIkeyは、載せておりませんので、文章生成はできなくなっております。(実行する場合には、api/routers内にてapikey.pyを作成し、key=に続けて入力してください)

## cd コマンドでapiに移動し、以下の順番でコードを実行する

$docker-compose build

$ docker-compose run --entrypoint "poetry install --no-root" demo-app

$ docker-compose build --no-cache

↓コンテナが動いた状態で

$ docker-compose exec demo-app poetry run python -m api.migrate_db

$docker-compose up


## データベースの確認方法

## 以下のコマンドをターミナルで順番に打つ

$ docker-compose exec db mysql demo

mysql> SHOW TABLES; (テーブルの確認)

mysql> DESCRIBE tasks;  (taskテーブルの中身を確認)

mysql> DESCRIBE dones;  (doneテーブルの中身を確認)

## dockerが立ち上がっている状態で以下のコードを実行する(ユニットテストの際に使用、-Dは開発者モードの時のみ実行される。デプロイ時には関係しない)
$docker-compose exec demo-app poetry add -D pytest-asyncio aiosqlite httpx
