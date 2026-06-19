# AI Writing Tools

Python、Streamlit、Gemini API で作る個人用 AI ライティングツールです。

## 機能

- ブログ記事作成
- メール返信作成
- 文章要約
- リライト
- SNS投稿作成
- 企画アイデア出し
- SEOタイトル・見出し作成
- 校正・改善

## セットアップ

```bash
python3.12 -m venv .venv312
source .venv312/bin/activate
pip install -r requirements.txt
export GEMINI_API_KEY="your_api_key"
streamlit run app.py
```

API キーはアプリのサイドバーから入力することもできます。入力されたキーはデータベースには保存されず、Streamlit のセッション内だけで使われます。

## 構成

- `app.py`: Streamlit アプリ本体
- `requirements.txt`: Python 依存パッケージ
- `.streamlit/config.toml`: Streamlit の表示設定
