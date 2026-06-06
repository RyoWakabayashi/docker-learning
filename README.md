# docker-learning

Docker学習用

Docker コンテナの基礎を学ぶための教材とハンズオン例をまとめたリポジトリです。新人エンジニアでも読み進めやすいように、専門用語の補足も入れています。

## 学習コンテンツ

- [Docker 基礎教材](docs/docker-basics.md)

## ハンズオン例

- [nginx で Web 配信](examples/nginx/README.md)
- [Jupyter をコンテナで起動](examples/jupyter/README.md)
- [PostgreSQL + pgAdmin](examples/postgres-pgadmin/README.md)

## おすすめの進め方

1. [Docker 基礎教材](docs/docker-basics.md) を上から読む
2. `Hello World` を実行する
3. `nginx` 例でコンテナから静的 Web 配信を試す
4. `Dockerfile` を編集して Web コンテンツを差し替える
5. `docker compose` で複数コンテナ構成を動かす
6. `Jupyter` 例でブラウザアプリをコンテナで起動し、ファイル共有を試す
7. `PostgreSQL + pgAdmin` 例で初期 DB、ネットワーク、ボリュームを確認する
