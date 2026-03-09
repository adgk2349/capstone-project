# Traveller (Capstone Project) - 日本語

[한국어](README.ko.md) | [English](README.en.md) | [Main README](README.md)

このリポジトリは、大学のキャップストーンチームプロジェクトとして開発された、位置情報ベースの旅行支援Webアプリケーションです。

## リポジトリ情報
- Fork元: `HSMighty7/Main`
- 現在のリポジトリ: `adgk2349/Traveller-Capstone_Project`
- Fork関係とコミット履歴を維持しています。

## 1) プロジェクト概要
`Traveller (Capstone Project)` は、ユーザーが観光地を検索し、現在地から目的地までのルートを可視化できるDjangoベースのサービスです。

## 2) 主な機能
1. ユーザー機能
- 新規登録、ログイン、ログアウト
- マイページ表示
- ユーザー名/パスワード変更

2. 検索機能
- 名前・住所によるキーワード検索
- カテゴリ別結果表示（観光地、レストラン、カフェ）
- ユーザー別検索履歴表示

3. 地図/経路機能
- 現在地の取得と保存
- 出発地から目的地までの経路可視化
- Foliumベースの地図レンダリング

## 3) 技術スタック
- Backend: `Python`, `Django 5`
- Geospatial: `OSMnx`, `NetworkX`, `Folium`, `GeoPandas`
- Database: Django ORM（`mighty7/my_settings.py`で設定）
- Frontend: Django Template, Bootstrap, CSS, JavaScript

## 4) プロジェクト構成
```text
capstone-project/
├── main/                    # コアアプリ (views, models, templates)
├── mighty7/                 # Django project settings/urls/wsgi
├── map/                     # 経路グラフ生成スクリプトとグラフデータ
├── static/                  # 静的リソース (css/js/img)
├── manage.py
├── requirements.txt
├── README.md
├── README.ko.md
├── README.en.md
└── README.ja.md
```

## 5) ローカル実行手順
1. リポジトリをクローン
```bash
git clone https://github.com/adgk2349/Traveller-Capstone_Project.git
cd Traveller-Capstone_Project
```

2. 仮想環境作成と依存関係インストール
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

3. `mighty7/my_settings.py` を作成
```python
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent

SECRET_KEY = {
    "secret": "replace-with-your-secret-key"
}

DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.sqlite3",
        "NAME": BASE_DIR / "db.sqlite3",
    }
}
```

4. マイグレーション実行とサーバー起動
```bash
python3 manage.py migrate
python3 manage.py runserver
```

5. ブラウザでアクセス
```text
http://127.0.0.1:8000
```

## 6) 主要ルート
- `/` : ホーム
- `/search` : スポット検索
- `/location` : 現在地の取得/保存
- `/map` : 経路可視化
- `/users/login/` : ログイン
- `/users/join/` : 新規登録
- `/users/mypage/` : マイページ
- `/users/update/` : アカウント情報更新

## 7) 補足
- `map/graph.osm` は経路可視化に使用するグラフデータです。
- グラフを再生成する場合は `python3 map/map.py` を実行してください。
