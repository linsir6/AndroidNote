````


1.  停止 mysql server.  通常是在 '系统偏好设置' > MySQL > 'Stop MySQL Server'
2.  打开终端，输入：sudo /usr/local/mysql/bin/mysqld_safe --skip-grant-tables
3.  sudo /usr/local/mysql/bin/mysql -u root
4.  UPDATE mysql.user SET authentication_string=PASSWORD('新密码') WHERE User='root';
5.  重启mysql
````
