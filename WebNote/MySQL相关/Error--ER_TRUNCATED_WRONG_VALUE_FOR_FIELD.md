![错误截图](http://upload-images.jianshu.io/upload_images/2585384-23615f16a18323d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 形如上面的错误，发生在向mysql数据库中插入中文的时候，编码格式遇到了问题，上Stack Overflow看了一下，应该是编码格式的问题。

解决方法是改变数据库的编码格式：

```
mysql> alter database test character set gbk;
```
这样我们数据库的编码格式就发生了改变，就可以插入中文了。但是原有已经有了的表还是不可以，因为已经有的表的编码格式还是默认的，所以需要将原有的表也改变一下：

```
mysql> alter table test character set gbk;
```

好了，到这问题就解决啦~~
