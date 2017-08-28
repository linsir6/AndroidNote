> mac的终端与远程服务器连接之后，可能由于一段时间没有与服务器进行数据上的交互便断开了连接，现在可以利用如下的方法，保持终端与远程服务器的长期连接。

编辑“ssh_config”文件：

```
sudo vi /etc/ssh/ssh_config

```

在Host *   下面加入:
```
ServerAliveInterval 60 
```

最后用``:wq!``保存并退出即可。

> 这句话的含义是，每隔60s客户端向服务器发送一个空包，这样就可以保持连接不被断开了。


![结果图](http://upload-images.jianshu.io/upload_images/2585384-9f41d4ffabedc4dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
