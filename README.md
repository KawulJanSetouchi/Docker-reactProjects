環境構築の手順
①Docker、nodeのインストール
②Dockerfile、docker-compose.ymlの作成
③ビルド
④Reactアプリの作成
⑤コンテナの実行

②Dockerfile、docker-compose.ymlの作成
docker-react-app（プロジェクトフォルダ）
　└┬─ Dockerfile
　　└─ docker-compose.yml

Dockerfile

FROM node:14.17.5 
WORKDIR /usr/src/app/

docker-compose.yml
docker-compose.yml
version: '3'
services:
  node:
    build:
      context: .
    tty: true
    environment:
      - NODE_ENV=development
    volumes:
    - ./:/usr/src/app
    command: sh -c "cd reactapp && npm start"
    ports:
    - "3000:3000"


    このコマンドを実行してビルドする。


docker-compose build

④Reactアプリの作成
docker-compose run --rm node sh -c "npm install -g create-react-app && create-react-app reactapp"







Success! Created reactapp at /usr/src/app/reactapp
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd reactapp
  npm start

Happy hacking!


⑤コンテナの実行
docker-compose up



ここまで完了したらWebブラウザで「 http://localhost:3000 」へアクセスする。以下のようにReactのページが起動すれば環境構築完了となる。
React-top