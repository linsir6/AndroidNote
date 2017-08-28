# React-Native 报错记录

- ``xxx is not defined``
    
    例如：``Component is not defined``
    错误原因：在当前的js文件中没有定义或者没有引入这个组建，并且有调用的地方
    
- ``JSX attributes must only assigned a non-empty expression(29:28)``
    
    错误原因：这个报错就非常简单了，已经告诉我们在哪一行了，错误原因就是，定义了之后不能为空
    
- ``Cannot read property 'Aspect' of undefined``

    错误原因：没有在当前文件夹下运行``react-native start``,导致一些关键的东西引入不进来

- ``undefined is not an object(evaluating 'Daily_Service.props.navigation')``

    错误原因：一般来说，我们这样写了代码，就是因为我们认为，可以用this,或者用到某个对象的时候，但是它本身是调用不了的。


- ``java.lang.illegalStateException:WebSocket connection no longer valid``

    错误原因，``react-native start``命令执行之后意外中断了
    
   





- ``在View添加了onPress，但是在点击的时候，不会产生任何效果``

    错误原因：View没有这样的方法，当遇到需要这样操作的方法的时候可以加入``<TouchableOpacity>  </TouchableOpacity>``
    
    


    
    
    
    


