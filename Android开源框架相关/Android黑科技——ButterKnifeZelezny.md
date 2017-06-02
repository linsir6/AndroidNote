> 先上一张效果图：

![效果图](https://raw.githubusercontent.com/avast/android-butterknife-zelezny/master/img/zelezny_animated.gif)


当一个XML中元素实在过多的时候，手动绑定id，不但浪费时间，而且非常的麻烦，有了这个黑科技之后，就可以轻松很多，解放双手啦。这是一个Android的插件，它是基于ButterKnife开发的，想要安装这个需要先添加Butterknife的 依赖，具体步骤如下：

----
## 添加Butterknife依赖

```
dependencies {
  compile 'com.jakewharton:butterknife:8.5.1'
  annotationProcessor 'com.jakewharton:butterknife-compiler:8.5.1'
}
```

```
buildscript {
  repositories {
    mavenCentral()
   }
  dependencies {
    classpath 'com.jakewharton:butterknife-gradle-plugin:8.5.1'
  }
}
```

```
apply plugin: 'com.android.library'
apply plugin: 'com.jakewharton.butterknife'
```

## 依赖添加完毕，安装插件


> in Android Studio: go to Preferences → Plugins → Browse repositories and search for ButterKnife Zelezny

安装完毕后，只需要重新启动一下studio，然后右键R.layout.activity_main，选择Generate，然后选择Generate ButterKnife Injections，就ok啦~






