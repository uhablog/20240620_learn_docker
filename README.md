# Docker&k8sについて学習する

## Dockerfile

### FROM

コンテナイメージのベースイメージを指定

### WORKDIR

コンテナ内のカレントディレクトリを指定、指定したディレクトリが存在しなければ、新しく作成される

### COPY

ビルドコンテキスト(コンテナイメージをビルドする環境のカレントディレクトリ)のファイルやディレクトリをコンテナ内にコピーする

### RUN

コンテナイメージビルド時に、コンテナ内で実行するコマンドを定義
パッケージのインストールやアプリケーションのビルドなどを記述

### CDM

コンテナが実行される際に、コンテナ内で実行するプロセスを指定
※実行時に上書きが可能

### ENV

環境変数の指定ができる

## コマンド

### docker image

- docker image build -t イメージ名[:タグ名] Dockerfile配置ディレクトリのパス: Dockerfileからイメージを作成する
- docker image tag 元イメージ[:タグ名] 新イメージ[:タグ名]
- docker image pull: イメージをコンテナレジストリから取得する
- docker image prue: イメージを削除できる

### docker container

- docker container run [option] [image_name]:[tag] -> docier imageをコンテナ実行する
- docker container run --name コンテナ名の指定 
- docker container prune: 停止中のコンテナの削除

### docker compose

- docker compose version -> docker composeのversion確認
- docker compose up -> compose.yamlによって、コンテナを起動
  - docker compose up -d -> バックグラウンドで実行
  - docker compose up --build -> dockerfileをビルドしてイメージを作成してからコンテナ実行(開発環境で頻繁にイメージ更新する際に必要)
- docker compose down -> コンテナを停止&削除

### その他
- docker search: イメージの検索が行える

## docker compose

- compose.yamlで定義
  - buildでDockerfileを指定して、サービス(コンテナ)を起動することができる

## 概念的な話

### イメージ

Dockerファイルを記述したら、ビルドすることで、作成される