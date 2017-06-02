# Kotlin for android

> 作者：https://github.com/linsir6
>
> 原文：http://www.jianshu.com/p/e713ba6f7c47



> kotlin最近真的是大热啊，总让人有一种不明觉厉的感觉，但是其实网上的学习资料少之又少，下面推荐几个学习的平台，顺便展示一个实现登录注册的demo



- [Kotlin 示例教程](https://github.com/linsir6/Kotlin)


- [kotlin中文官网](https://www.kotlincn.net/)
- [kotlin官网](https://kotlinlang.org/)
- [kotlin官网翻译](https://github.com/huanglizhuo/kotlin-in-chinese)
- [kotlin书籍](https://github.com/wangjiegulu/kotlin-for-android-developers-zh)
- [kotlin demo](https://github.com/linsir6/PoiShuhui-Kotlin)



下面就我们就开始一个入门级别的demo吧，现在谷歌已经推出了android studio3.0已经支持了Kotlin这门语言，下载地址：https://developer.android.google.cn/studio/preview/index.html ，只需要在这里新建一个工程，然后在是否要加入kotlin的选项上面勾一下就可以了。





下面看一下登录注册的代码：

```kotlin
class MainActivity : AppCompatActivity() {

    var userName: EditText? = null
    var userPwd: EditText? = null
    var register: Button? = null
    var login: Button? = null

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        userName = findViewById(R.id.user_name) as EditText
        userPwd = findViewById(R.id.user_pwd) as EditText

        register = findViewById(R.id.register) as Button
        login = findViewById(R.id.login) as Button

        login!!.setOnClickListener {
            if (userName!!.text.toString() == "123456" && userPwd!!.text.toString() == "abc") {
                Toast.makeText(this, "login succeed1", Toast.LENGTH_SHORT).show()
                val intent = Intent(this,HomeActivity::class.java)
                startActivity(intent)
            }
        }

        register!!.setOnClickListener {
            Toast.makeText(this, "the function has not open ...", Toast.LENGTH_SHORT).show()
        }

    }

}


```





当然实现的代码就非常简单啦，只是可能我们在刚开始接触这门语言的时候有一些的不理解。大家可以看一下上面的代码，要是有什么不理解的地方欢迎issue。



源码地址：https://github.com/linsir6/Kotlin

欢迎star，issue，fork





























