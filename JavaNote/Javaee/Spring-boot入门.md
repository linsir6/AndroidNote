# Spiring-boot入门

> 最入门级别的Spring框架，省了很多配置的过程，比较适合初学者，或者微站的使用，所以打算从这里开始学起。

学习的地址：https://www.bysocket.com/?p=1627

包目录结构：

![](https://ws1.sinaimg.cn/large/006tNc79ly1flcxydakxlj30km0zyt9d.jpg)

这里面分了很多层，主要有的层就是，controller,dao,domain,service,Application。

SpringBoot的优势就在于它内置了TomCat,并且不需要过多的配置就可以直接使用，也不用配置Spring那一套。

这次实现的是springboot-restful的过程，rest是web的一种框架风格，主要用于前后端分离。

首先我们要实现一个controller，这里面负责拦截用户的url，然后可以设置是GET还是POST的方法，同时我们还需要实现一个dao层，这层是用来负责数据持久化的，简单说就是这里和数据进行的直接接触。接下来要实现一个domain层，这一层大家应该都能明白有的时候我们叫它model有的时候叫它bean，接下来就要实现service层了，这一层中我们需要定义一个接口，并且编写一个它的实现类就可以了，我们在controller中调用的便是这一层的内容。

其实我们的代码，以上便已经编写完成了，但是我们还有几个点是没有完成的，我们的sql语句还没有配置呢。我们需要在resources/mapper/CityMapper.xml内中写入。在resources/application.properties中写入数据库的信息，配置一下就好。

代码地址：https://github.com/linsir6/Javaee-Spring-demo

博主在Spring方面也是刚刚起步的小菜鸟，写以上内容只是为了，记录学习笔记，要是有什么错误，欢迎大家提出指正。
