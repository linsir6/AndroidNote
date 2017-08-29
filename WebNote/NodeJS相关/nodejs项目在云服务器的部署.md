> 最近写了个小小的网站，折腾了好久啦，最开始使用Python的flask写的，后来感觉不是很方便于维护，而且想试试nodejs，就重新写了一遍，当然工程很小，两三天就写完了，不过中间也是吃了不少苦，掉了很多根头发的。下面为大家介绍一下nodejs怎么部署。

> 良心的我，还是要给腾讯云打波广告的，原价65的云服务器，配置还可以，还有公网ip的，学生优惠只需要1元钱，全部审核过程只用了不到五分钟，总而言之非常nice。

1. 打开控制台，利用ssh命令连接上服务器

````
ssh ubuntu@139.199.177.20
````
----
2.看到这样的字样就代表登录成功啦

````
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-53-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

````
----
3.我们下载包的管理工具，并且更新一下数据源
````
sudo apt install yum
````
以上在下载yum包管理工具

----

4.进入/usr/src路径，下载nodejs并解压
````
cd /usr/src 
sudo wget http://nodejs.org/dist/v0.10.18/node-v0.10.18.tar.gz 
tar zxf node-v0.10.18.tar.gz 
````
----
5.进入到解压完的文件,执行编译预处理，开始编译
````
cd node-v0.10.18
./configure
sudo make
````
----
6.执行make install，nodejs就安装完毕了
````
sudo make install
````

----
7.安装forever，安装完成后，建立软连接
````
npm -g install express forever

sudo ln -s /usr/local/bin/node /usr/bin/node 
sudo ln -s /usr/local/lib/node /usr/lib/node 
sudo ln -s /usr/local/bin/npm /usr/bin/npm 
sudo ln -s /usr/local/bin/node-waf /usr/bin/node-waf 
sudo ln -s /usr/local/bin/forever /usr/bin/forever
````
----
8.只需要上传我们的代码，然后运行就可以啦
运行：
````
sudo forever start server.js
````

查看应用列表：
````
sudo forever list
````

关闭应用：
````
sudo forever stop 0
````













