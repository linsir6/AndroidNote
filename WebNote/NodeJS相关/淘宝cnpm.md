> 在国内使用npm是非常慢的，但是我们可以使用淘宝的镜像cnpm。

这个镜像，是一个完整的，同步镜像，所以我们可以完全使用cnpm来代替npm。

----
安装npm：
````
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
````
之后就可以在使用npm的时候，用cnpm来替代了。

````
$ cnpm install [name]
````
