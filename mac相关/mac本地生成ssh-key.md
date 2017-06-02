进入当前路径
```
/Users/mac/.ssh/
```


![拥有id_rsa.pub](http://upload-images.jianshu.io/upload_images/2585384-4dfd502b058245c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果没有这个文件的话：
```
ssh-keygen -t rsa -C "youremail@example.com"
```

然后会有几个提示的问题，都可以不用管，直接回车就可以，完成之后这里面就会生成公钥。

如果要是github要配置的话，只需要在账户的setting里面进行设置就可以(将.pub文件用文本阅读工具打开，然后全部复制粘贴到new ssh key就好)，如下图：


![成功后的效果图](http://upload-images.jianshu.io/upload_images/2585384-aed9e786307f6fc9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
