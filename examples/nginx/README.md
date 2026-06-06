# nginx ハンズオン

このディレクトリでは、`Dockerfile` から独自の `nginx` イメージを作り、コンテナから静的 Web コンテンツを配信します。

## ファイル構成

- `Dockerfile`
- `index.html`
- `compose.yaml`

## 1. イメージをビルドする

```bash
docker build -t docker-learning-nginx .
```

## 2. コンテナを単体起動する

```bash
docker run --name docker-learning-nginx -d -p 8080:80 docker-learning-nginx
```

ブラウザで `http://localhost:8080` を開いて表示を確認します。

状態確認:

```bash
docker ps
docker logs docker-learning-nginx
```

後片付け:

```bash
docker stop docker-learning-nginx
docker rm docker-learning-nginx
```

## 3. Compose で起動する

```bash
docker compose up -d
docker compose ps
docker compose logs -f
```

停止:

```bash
docker compose down
```

## 4. 学習ポイント

- `Dockerfile` で既存 image をベースに独自コンテンツを追加できる
- `ports` でホストからコンテナへアクセスできる
- `docker logs` で Web サーバーのアクセス状況を確認できる
