# rails_and_mysql_on_docker_for_mac
Docker for MacにRuby on RailsとMysql 8.0の環境を作成する

参考：https://qiita.com/Nishi53454367/items/aee4cf0c346bc115be99

Step1
docker-compose run web rails new . --force --database=mysql

Step2
docker-compose build --no-cache

Step3[db ホストとパスワードをdocker-compose.ymlに合わせて修正]
vi config/database.yml password and host

--------begin--------
default: &default
  adapter: mysql2
  encoding: utf8
  pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
  username: root
  password: password <<-- Here
  host: db <<-- Here
--------end--------

Step4
docker-compose run web rake db:create

Step5
docker-compose up -d

確認
http://localhost:3000
