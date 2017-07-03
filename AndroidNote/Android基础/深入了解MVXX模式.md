# 深入了解MV**模式


**MVXX模式：**

- MVC
- MVP
- MVVM

这三种架构模式都是现在比较流行的，在不同的项目中，可能采用不同的架构模式，今天我们就围绕着这三种架构模式的试用场景介绍一下他们的概念，以及异同。

## MVC

MVC(Model-View-Controller),Model:逻辑模型，View:视图模型，Controller控制器。



## MVP


Model(Model View Presenter),Model:逻辑模型，View:视图模型，Presenter:不知道。

关于MVP的定义：
    
    - MVC的演化版本，让Model和View完全解耦
    - 代码清晰，不过增加了很多类
    
    
在Android中，我们的View可能仅仅就是个布局文件，它能做的事情少之又少，真正与布局文件进行数据绑定操作的事Activity，所以这样做就使Activity即像View又像Controller。    

应用了MVP之后：

    - View:对应Activity，负责View的绘制以及与用户交互
    - Model:业务逻辑和实体模型
    - Presenter:负责完成View与Model之间的交互



应用两张图来说明上述内容:

![](http://img.blog.csdn.net/20150622212835554)

![](http://img.blog.csdn.net/20150622212856011)



### MVP与MVC区别

如下图所示：

![](http://img.blog.csdn.net/20150622212916054)





## 相关资料

- 浅谈[MVP in Android](http://blog.csdn.net/lmj623565791/article/details/46596109)
