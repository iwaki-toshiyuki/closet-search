# closet-search

Django + Docker を使った開発環境です。

## 📦 必要要件

- Docker
- Docker Compose

---

## 🚀 セットアップ手順

### 1. リポジトリをクローン

```bash
git clone https://github.com/iwaki-toshiyuki/closet-search.git
cd closet-search
```

### 2. .env を作成

.env.example を元に .env を作成します

```bash
cp .env.example .env
```

### 3.Django プロジェクトを起動

以下のコマンドでコンテナをビルド＆起動します：

```bash
docker-compose up --build
```

### 4.マイグレーションの適用
```bash
docker-compose exec django python manage.py migrate
```

### 5.ブラウザで動作確認
以下の URL にアクセスします：

👉 http://localhost:8000

「The install worked successfully!」と表示されれば、セットアップ成功です。
