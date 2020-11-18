Djangoプロジェクト
====================


初期処理
----------

プロジェクト環境構築時に１回だけ行う作業

```bash
# dockerコンテナビルド
docker-compose build

# dockerコンテナ内でdjango環境構築
docker run --rm -it -v /$(pwd)://src -w //src --entrypoint //bin/bash my-django
/src# django-admin startproject config .

# DBマイグレーション&管理者ユーザ作成
/src# python manage.py migrate
/src# python manage.py createsuperuser
```


使い方
----------

### Docker操作方法
```bash
# docker環境の構築&起動
docker-compose up -d

# docker環境の破棄
docker-compose down -v

# docker環境の停止
docker-compose stop

# docker環境の再開
docker-compose start
```

### DBマイグレーション

dockerコンテナ内でマイグレーションコマンドを実行する

```bash
docker-compose exec django //bin/bash
(container)# python manage.py migrate
```


PyChramへの設定
----------

### プロジェクト

* Python インタープリター
	- プロジェクトディレクトリ内の`docker-compose.yml`と`django`を指定する
* プロジェクト構成
	- 任意で設定

### 言語 & フレームワーク

* Django
	- ☑Django サポートを使用可能にする
	- Django プロジェクトルート: `project/`ディレクトリを指定
	- 設定: `config`\settings.py`を指定

### 実行/デバッグ構成

Djangoサーバーを新規追加する

* 名前: 任意で設定
* 構成
	- ホスト: 0.0.0.0
	- ☑ブラウザーの実行: http://127.0.0.1:8000/
	- Python インタープリター: プロジェクトで設定したインタープリターを指定
	- パスマッピング: .=/src

