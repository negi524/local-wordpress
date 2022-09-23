# local-wordpress
WordPressのローカル開発環境

## 起動方法

### 1. コンテナを起動する

```bash
docker compose up -d
```

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

任意のユーザー名、パスワード、メールアドレスを持ちいてWordPressの初期設定を行う。