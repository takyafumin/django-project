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
```


使い方
----------

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

