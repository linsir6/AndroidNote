1.linux下安装mysql：
````
sudo apt-get update
sudo apt-get install mysql-client-core-5.6
sudo apt-get install mysql-client-5.6
sudo apt-get install mysql-server-5.6
````

以上便是安装MySQL的全过程了。

----
2.查看是否运行：
````
ps -ef | grep mysql
````
----
3.MySQL的停止：
````
sudo service mysql stop
````
----
4.MySQL的开启：
````
sudo service mysql start
````
----
5.MySQL的重启：
````
service mysql restart
````
----
6.MySQL的登录
````
mysql -u root -p #这里面的root是用户名
````









