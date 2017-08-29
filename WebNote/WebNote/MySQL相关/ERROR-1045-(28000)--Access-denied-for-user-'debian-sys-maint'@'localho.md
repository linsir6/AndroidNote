> 原本linux（Ubuntu）上面安装mysql是非常简单的事情，但是我今天真是b了狗了，装个mysql，运行各种失败，希望大家以后遇到这个问题别这么难过啦。


````
ERROR 1045 (28000): Access denied for user 'ubuntu'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'ubuntu'@'localhost' (using password: NO)
````


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2585384-3889166b952adcb3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![Paste_Image.png](http://upload-images.jianshu.io/upload_images/2585384-7adc01e923ec74f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其实这里面提供了，我们可以登录的账号密码，只需要暂时用这个登录，然后再授权一个新用户就行。

以上便是这个问题的解决方案啦。





