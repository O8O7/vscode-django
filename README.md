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
coverage report -m --skip-covered # 網羅率100%のファイルをスキップ
coverage html # htmlとしてレポートを出力
```

## settings.pyの設定

```python

# Templates
# "DIRS": [BASE_DIR / "templates"]

LANGUAGE_CODE = "ja"

TIME_ZONE = "Asia/Tokyo"

STATIC_URL = "/static/"

STATICFILES_DIRS = [
    BASE_DIR / "static",
]

MEDIA_URL = "/media/"
MEDIA_ROOT = BASE_DIR / "media"

# ログ出力先のディレクトリを設定する
if DEBUG:
    LOG_BASE_DIR = Path(BASE_DIR / "logs")
else:
    LOG_BASE_DIR = Path("/var/log/app")

LOGGING = {
    "version": 1,
    "disable_existing_loggers": False,
    "formatters": {"simple": {"format": "%(asctime)s [%(levelname)s] %(message)s"}},
    "handlers": {
        "info": {
            "level": "INFO",
            "class": "logging.FileHandler",
            "filename": LOG_BASE_DIR / "info.log",
            "formatter": "simple",
        },
        "warning": {
            "level": "WARNING",
            "class": "logging.FileHandler",
            "filename": LOG_BASE_DIR / "warning.log",
            "formatter": "simple",
        },
        "error": {
            "level": "ERROR",
            "class": "logging.FileHandler",
            "filename": LOG_BASE_DIR / "error.log",
            "formatter": "simple",
        },
    },
    "root": {
        "handlers": ["info", "warning", "error"],
        "level": "INFO",
    },
}

```