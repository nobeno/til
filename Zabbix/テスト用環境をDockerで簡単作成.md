## テスト用環境をDockerで簡単作成

### https://www.zabbix.org/wiki/Dockerized_Zabbix

1. データベース用コンテナ
```
docker run \
   -d \
   --name dockbix-db \
   -v /etc/localtime:/etc/localtime:ro \
   --env="MARIADB_USER=zabbix" \
   --env="MARIADB_PASS=my_password" \
   monitoringartist/zabbix-db-mariadb
```

2. サーバ用コンテナ
```
docker run \
   -d \
   --name dockbix \
   -p 80:80 \
   -p 10051:10051 \
   -v /etc/localtime:/etc/localtime:ro \
   --link dockbix-db:dockbix.db \
   --env="ZS_DBHost=dockbix.db" \
   --env="ZS_DBUser=zabbix" \
   --env="ZS_DBPassword=my_password" \
   --env="XXL_zapix=true" \
   --env="XXL_grapher=true" \
   monitoringartist/dockbix-xxl:latest
```

3. ログ確認
```
docker logs dockbix
```

4. 削除
```
docker rm zabbix zabbix-db
```

