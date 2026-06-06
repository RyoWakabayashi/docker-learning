# Jupyter ハンズオン

このディレクトリでは、JupyterLab をコンテナで起動し、ブラウザから notebook を開く流れを体験します。

## この例で学べること

- ブラウザアプリをコンテナで起動する
- `docker compose` で起動設定を固定化する
- ローカルのフォルダをコンテナにマウントして notebook を保存する

## ファイル構成

- `compose.yaml`
- `work/welcome.ipynb`

## 1. 起動する

```bash
docker compose up -d
```

初回は Jupyter イメージのダウンロードがあるため、少し時間がかかることがあります。

状態確認:

```bash
docker compose ps
docker compose logs -f
```

## 2. ブラウザで開く

次の URL を開きます。

- JupyterLab: [http://localhost:8888/lab?token=learn-docker](http://localhost:8888/lab?token=learn-docker)

## 3. notebook を触る

`work/welcome.ipynb` を開くと、最初の notebook が入っています。

この `work` フォルダはホスト側の `examples/jupyter/work` とつながっているので、作成した notebook はローカルにも保存されます。

## 4. 停止する

```bash
docker compose down
```

## 5. 学習ポイント

- コンテナの中で Web アプリを動かし、ブラウザから利用できる
- `volumes` を使うと notebook ファイルをホスト側へ残せる
- ローカルに Python を大量インストールしなくても、分析環境をすぐ試せる
