## VSCodeの設定でセーブ時にPythonをblackでフォーマット、isortでimportの順序を整頓


> 仮想環境作成andアクティブ化

### mac
```bash
python3 -m venv venv
source venv/bin/activate
```

### windows
```bash
python -m venv venv
./venv/Scripts/activate
```
---

> 開発環境にrequirements-dev.txtインストール

```bash
pip install -r requirements-dev.txt
pip freeze > requirements-dev.txt
```
---

> flake8のコードスタイルチェックコマンド

[flake8 Github](https://github.com/PyCQA/flake8)

```bash
flake8 # プロジェクト全体
flake8 {ファイル名 or ディレクトリ名} # ファイル単体かディレクトリ名単体
```

> blackでコードをフォーマット

[black Github](https://github.com/psf/black)

```bash
python -m black {ファイル名 or ディレクトリ名} --check
```

---

> coverageでテストのカバレッジを取得

[coverage Github](https://github.com/nedbat/coveragepy/blob/6.4.1/doc/index.rst)

```bash
coverage run --source='.' manage.py test

coverage report # カバレッジレポート表示
```