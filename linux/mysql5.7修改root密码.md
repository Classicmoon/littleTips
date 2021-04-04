# mysql5.7修改root密码  
step1：修改my.cnf配置文件  
```
  vi /etc/my.cnf
  在[mysqld]下边的某个位置增加：skip-grant-tables,然后:wq保存退出
```
step2：重启并使用root账户连接mysql  
```
  service mysqld restart
  mysql -u root -h 127.0.0.1
```
step3；修改root密码  
```
  use mysql;
  SET SQL_SAFE_UPDATES = 0;
  update mysql.user set authentication_string=password('newpassword') where User='root';
  flush privileges;
  SET SQL_SAFE_UPDATES = 1;
```
step4：还原配置文件并重启mysql  
```
  vi /etc/my.cnf，删除skip-grant-tables项并保存
  service mysqld restart
```
现在可以使用新的root密码连接mysql了。  
