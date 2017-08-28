1.首先应该检测一下目前电脑上拥有的java的版本：
````
/usr/libexec/java_home -V
````
----

2.如果已经有java8了，就可以直接跳转到第四步：

![拥有java1.8](http://upload-images.jianshu.io/upload_images/2585384-067a0e7b037c14dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

----

3.没有java1.8，需要上网下载java1.8：
下载链接：http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

----

4.配置当前环境：
````
vi .bash_profile  #打开配置的文件
source .bash_profile #当配置完成后运行，让配置生效
````
配置语句，可以参考我的这个：
````
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_121.jdk/Contents/Home
export PATH=$COCOS_CONSOLE_ROOT:$JAVA_HOME/bin:$PATH:.
export CLASSPATH=$JAVA_HOME/lib/tools.jar:$JAVA_HOME/lib/dt.jar:.
````

给大家截个图看一下吧：

![配置截图](http://upload-images.jianshu.io/upload_images/2585384-a010212ee14ef7e2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

当配置完千万要记得，要运行上面那条语句让整个文件生效。

5.检查当前java版本：
````
java -version
````
就能看到我们配置的版本啦~
````
java version "1.8.0_121"
Java(TM) SE Runtime Environment (build 1.8.0_121-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.121-b13, mixed mode)
````













