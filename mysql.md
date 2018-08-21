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

### mysql
```
# To connect to a database
mysql -h localhost -u user -D database -P 3306 -p

# To create a database in utf8 charset
CREATE DATABASE owa CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;

# To add a user and give rights on the given database
GRANT ALL PRIVILEGES ON database.* TO 'user'@'localhost'IDENTIFIED BY 'password' WITH GRANT OPTION;
```
