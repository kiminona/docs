### テーブル一覧
```
show tables;
```
### ビルド
```bash
# diesel
MYSQLCLIENT_LIB_DIR: C:\Program Files\MySQL\MySQL Server 5.7\lib
# mysql
mysql://user:pass@host:port/name?prefer_socket=false
```

### GRANT構文の実行権限をもつユーザを作成
```sql
CREATE DATABASE データベース名;
GRANT ALL PRIVILEGES ON データベース名.* TO ユーザー名@localhost IDENTIFIED BY 'パスワード';
FLUSH PRIVILEGES;
```
### mysql client

```
mysql -h localhost -u user -p
```
