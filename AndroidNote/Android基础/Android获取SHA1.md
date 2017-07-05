# Android获取SHA1



1. 在Android Studio中打开Terminal或者进入控制台
2. cd到jdk的bin目录下
3. 输入命令 ``keytool -list -keystore /Users/mac/WorkSpace/linGitHub/Daily/key/fuyizhulao.jks``
4. 上面这个命令，大家需要选择自己的jks文件
5. 输入密码
6. 然后就可以看到自己的证书指纹(SHA1)了


效果图：


![](https://ws1.sinaimg.cn/large/006tNbRwly1fh96jjtx73j31dk0q2gnw.jpg)