# PostgreSQL + pgAdmin ハンズオン

このディレクトリでは、`docker compose` で PostgreSQL と pgAdmin をまとめて起動し、初期 DB 構築、ネットワーク、ボリュームを確認します。

## ファイル構成

- `compose.yaml`
- `.env.example`
- `initdb/001_schema.sql`
- `initdb/002_seed.sql`

## 1. 環境変数ファイルを用意する

```bash
cp .env.example .env
```

必要なら `.env` の値を変更します。

## 2. 起動する

```bash
docker compose up -d
```

状態確認:

```bash
docker compose ps
docker compose logs -f
```

## 3. アクセス先

- PostgreSQL: `localhost:5432`
- pgAdmin: `http://localhost:8081`

pgAdmin のログイン情報は `.env` の `PGADMIN_DEFAULT_EMAIL` と `PGADMIN_DEFAULT_PASSWORD` を使います。

## 4. pgAdmin から PostgreSQL に接続する

pgAdmin にログインしたら、Server を追加して次のように設定します。

- Name: `local-postgres`
- Host name/address: `postgres`
- Port: `5432`
- Maintenance database: `.env` の `POSTGRES_DB`
- Username: `.env` の `POSTGRES_USER`
- Password: `.env` の `POSTGRES_PASSWORD`

ここで `localhost` ではなく `postgres` を使うのがポイントです。これは Compose ネットワーク上のサービス名です。

## 5. 初期データ

初回起動時、`initdb` 配下の SQL が PostgreSQL コンテナ内で自動実行されます。

このサンプルでは次を行います。

- `products` テーブルの作成
- 初期データ 3 件の投入

確認用 SQL:

```sql
SELECT * FROM products ORDER BY id;
```

## 6. ボリューム

この構成では 2 つの named volume を使っています。

- `postgres_data`: PostgreSQL の永続データ
- `pgadmin_data`: pgAdmin の設定や接続情報

確認コマンド:

```bash
docker volume ls
```

## 7. ネットワーク

この構成では `postgres-pgadmin-network` という bridge ネットワークを使っています。

確認コマンド:

```bash
docker network ls
docker network inspect postgres-pgadmin-network
```

## 8. 停止と削除

```bash
docker compose down
```

ボリュームも消して初期化したい場合:

```bash
docker compose down -v
```
