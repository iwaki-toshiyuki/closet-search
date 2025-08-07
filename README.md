# Style Log

https://style-log.com/

## 📦 必要要件
Django + Docker を使った開発環境です。

- Docker
- Docker Compose

---

## 🚀 セットアップ手順

### 1. リポジトリをクローン

```bash
git clone git@github.com:summer-hackathon-c/closet-search.git
cd closet-search
```

### 2. .env を作成

.env.example を元に .env を作成します

```bash
cp .env.example .env
```

Windowsの場合は
```bash
copy .env.example .env
```

### 3.Django プロジェクトを起動

以下のコマンドでコンテナをビルド＆起動します：

開発環境用
```bash
docker compose -f docker-compose.dev.yml up --build -d
```

本番環境用
```bash
docker compose -f docker-compose.prod.yml up --build -d
```

### 3.1 マイグレーション（DBテーブル作成）
buildのマイグレーションでエラーが起きたら、単独で以下のマーグレーションコマンド試しても良いかもしれません。

#### 3.1.1. マイグレーションファイルを作成
```bash
docker compose -f docker-compose.dev.yml exec django python manage.py makemigrations
```

#### 3.1.2. マイグレーションを実行（テーブル作成など）
```bash
docker compose -f docker-compose.dev.yml exec django python manage.py migrate
```


### 4.ブラウザで動作確認
以下の URL にアクセスします：

👉 http://localhost:8000

「The install worked successfully!」と表示されれば、セットアップ成功です。

### 5.Djangoプロジェクト削除

開発環境用
```bash
docker compose -f docker-compose.dev.yml down
```

本番環境用
```bash
docker compose -f docker-compose.prod.yml down
```

### 6.コンテナ内部に入るコマンド

Django コンテナ
```bash
docker compose -f docker-compose.dev.yml exec django /bin/bash
```

MySQL コンテナ
```bash
docker compose -f docker-compose.dev.yml exec db /bin/bash
```

### 7.コンテナ内から MySQL にログイン
```bash
docker compose -f docker-compose.dev.yml exec db mysql -uapp_user -papp_pass app_db
```

### 8.Ruffコマンド

Lint(コードチェック& 自動修正)

```bash
make lint
```

Lint(コードチェックのみ)

```bash
make lint-check
```

Format（コード整形）

```bash
make format
```

### 9.コンテナの状態を確認コマンド

```bash
docker compose -f docker-compose.dev.yml ps
```

### 10.ログ確認コマンド（エラーが出た時に試してください。）

Django アプリのログを確認

```bash
docker compose -f docker-compose.dev.yml logs -f django
```

MySQL コンテナのログを確認
```bash
docker compose -f docker-compose.dev.yml logs -f db
```
