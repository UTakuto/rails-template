# 🚀 Rails Template with Docker

このリポジトリは、Docker 環境上で Ruby on Rails を素早く立ち上げるためのテンプレートです。MySQL と連携済みで、開発初期のセットアップ時間を大幅に短縮できます。

---

## 📦 使用技術

-   **Ruby on Rails**
-   **MySQL**
-   **Docker / Docker Compose**

---

## 📁 ディレクトリ構成

```
.
├── Dockerfile             # Railsアプリ用のDockerfile
├── compose.yml            # Docker Compose設定
├── .env                   # 環境変数（ポートやDB設定など）
├── .gitignore
├── Gemfile                # Rails依存管理
├── Gemfile.lock
├── db_data/               # MySQLデータの永続化ボリューム
└── README.md
```

---

## 🛠 セットアップ手順

### 1. リポジトリをクローン

```bash
git clone https://github.com/UTakuto/rails-template.git
cd rails-template
```

### 2. `.env` を編集（必要に応じて）

```env
MYSQL_ROOT_PASSWORD=your_password
MYSQL_DATABASE=your_db_name
MYSQL_USER=your_user
MYSQL_PASSWORD=your_password
```

### 3. Docker で環境構築

```bash
docker compose build
docker compose up -d
```

### 4. コンテナに入って Rails 初期化

```bash
docker compose exec web rails db:create db:migrate
```

---

## 🌐 アクセス

-   Rails: [http://localhost:3000](http://localhost:3000)
-   phpMyAdmin（設定がある場合）: `localhost:8080`（別途構成必要）

---

## 🧹 補足

-   `db_data` フォルダは MySQL のデータ永続化用です。Git には含めないよう `.gitignore` 済みです。
-   初回起動時に `Gemfile.lock` や `db_data` が無いとエラーが出る場合があります。必要に応じて削除して再ビルドしてください。
