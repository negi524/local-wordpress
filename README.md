# local-wordpress
WordPressのローカル開発環境

## ディレクトリ構成
```bash
$ tree . -L 1
.
├── README.md
├── docker-compose.yml  # Compose定義ファイル
└── html  # コンテナ内のWordPressファイルとホストマシンを共有するためのディレクトリ
```


## 初回起動方法

### 1. コンテナを起動する

```bash
docker compose up -d
```

* `-d`：バックグラウンドで実行するオプション

コンテナが起動されていればOK

```bash
$ docker container ls
CONTAINER ID   IMAGE              COMMAND                  CREATED       STATUS         PORTS                  NAMES
1f6ff631754f   wordpress:latest   "docker-entrypoint.s…"   5 hours ago   Up 3 seconds   0.0.0.0:8080->80/tcp   local-wordpress-wordpress-1
77c012a72f83   mysql:8.0.27       "docker-entrypoint.s…"   5 hours ago   Up 3 seconds   3306/tcp, 33060/tcp    local-wordpress-db-1
```

### 2. 起動されていることを確認する

`http://localhost:8080`にアクセスする。

### 3. WordPressの初期設定を実施

任意のユーザー名、パスワード、メールアドレスを用いてWordPressの初期設定を行う。

#### テスト用アカウント

| 項目       | 値       |
|:----------:|:--------:|
| ユーザー名 | user1    |
| パスワード | passw0rd |

### 4. テストデータを投入する

TODO


### 5. WordPress REST APIが利用できるように設定する

TODO

## 停止方法

```bash
docker compose stop
```

## 再起動方法

```bash
docker compose start
```

## データの削除・初期化

### 1. Compose定義ファイルから作成されたコンテナやボリュームなどを削除

```bash
docker compose down --rmi all -v
```

* `--rmi all`：全てのイメージを削除
* `-v`：Compose定義ファイルのデータボリュームを削除


### 2. ホストマシンと共有しているファイル削除

```bash
rm -r ./html/*
```

```bash
rm ./html/.htaccess
```

## テストデータの用意

https://github.com/jawordpressorg/theme-test-data-ja

## 参考
https://docs.docker.com/samples/wordpress/
