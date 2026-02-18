[README.md](https://github.com/user-attachments/files/25386576/README.md)
# My Dairy

Flask と PostgreSQL を使用して作成した日記アプリ(CRUD/ログイン機能あり)です．
ログインしたユーザーのみが日記の作成・編集・削除を行うことができます．

---

## スクリーンショット

### トップページ
<img src="Diary/screenshot/toppage.png" width="600">

### ログインページ
<img src="Diary/screenshot/login.png" width="600">

### 日記作成
<img src="Diary/screenshot/create.png" width="600">

### 日記編集
<img src="Diary/screenshot/edit_option.png" width="600">
<img src="Diary/screenshot/edit.png" width="600">

---

## 機能一覧
- 日記一覧表示
- 日記詳細表示
- ユーザー登録
- ログイン / ログアウト
- 日記のCRUD機能
- 管理者ページ（ログイン必須）

---

## 使用技術
- Python
- Flask
- PostgreSQL
- HTML
- CSS

---

## 環境構築(MacOS)

### ①前提環境
- Python 3.x
- PostgreSQL（インストール済み＆起動済みであること）

### macOS で PostgreSQL を入れる
```bash
brew install postgresql
brew services start postgresql
```


### ②リポジトリのクローン
```bash
git clone https://github.com/Urara2438/Diary_app.git
cd Diary_app
```
### ③仮想環境の作成と有効化
```bash
python -m venv .venv
source .venv/bin/activate
```

### ④依存関係のインストール
```bash
pip install flask flask_sqlalchemy flask_migrate flask_login "psycopg[binary]"
```

### ⑤データベース設定
本アプリは main.py 内の DB_INFO に書かれた接続情報を使います．
自分の環境に合わせて以下を編集してください．

- user（PostgreSQLのユーザー名）
- password（PostgreSQLのパスワード）
- name（使用するデータベース名）

例：name を diary_db にする場合，以下をターミナルで実行し，PostgreSQL側でDBを作成します．
```bash
createdb diary_db
```

### ⑥テーブル作成
```bash
python
>>> from main import app, db
>>> with app.app_context():
...     db.create_all()
```

### ⑦アプリケーション起動
```bash
flask --app main run
```
### ⑧ブラウザでアクセス
ブラウザで以下にアクセスします。
http://127.0.0.1:5000/

---

## ルーティング一覧

| URL              | 内容     |
| ---------------- | ------ |
| `/`              | Top page (日記一覧) |
| `/<id>/readmore` | Readmore (記事詳細) |
| `/signup`        | Signup (ユーザー登録) |
| `/login`         | Login (ログイン) |
| `/logout`        | Logout (ログアウト) |
| `/admin`         | My page (マイページ) |
| `/create`        | Create diary (日記作成) |
| `/edit_option`   | Edti dairies (日記編集一覧) |
| `/edit`          | Edti dairy (日記編集) |
| `/delete_option` | Delete diaries (日記削除一覧) |
| `/delete`        | Delete diary (日記削除) |

---

## ディレクトリ構成
```bash
.
├── main.py
├── templates/
├── static/
│   └── img/
│   └── css/
├── migrations/
└── README.md
```
---

## 今後の改善点
- 管理者と一般ユーザーの権限の分離
