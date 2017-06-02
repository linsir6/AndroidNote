> 在命令行下导出数据库、表(有无数据)具体用法如下： 

```
mysqldump -u用戶名 -p密码 -d 数据库名 表名 > 脚本名;
 ```


![效果图](http://upload-images.jianshu.io/upload_images/2585384-8acc14df2492d804.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


---

导出整个数据库结构和数据:
```
mysqldump -h localhost -uroot -p123456 database > dump.sql
```
 ----

导出单个数据表结构和数据:

```
mysqldump -h localhost -uroot -p123456  database table > dump.sql
```
 ---

 

导出整个数据库结构（不包含数据）:

```

mysqldump -h localhost -uroot -p123456  -d database > dump.sql

 ```
----

导出单个数据表结构（不包含数据）:

```
mysqldump -h localhost -uroot -p123456  -d database table > dump.sql

```

----
如果提示权限异常，请注意，是否在当前目录下具有写文件的权利，如果没有可以切换到别的目录下面，再执行这个操作。
