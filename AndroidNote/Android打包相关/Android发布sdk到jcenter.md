# Android发布sdk到jcenter

> 当我们写好一个开源项目或者写好一个商用的sdk的时候，我们可能需要将它上传到jcenter这样可以更好的提供给别人或者用户使用。当我们们上传之后，用户便可以在gradle里面通过compile来引用我们的项目了。

本文介绍的是通过`bintray-release`这个插件来上传我们的项目。



### 1. 注册bintray账号

[注册链接](https://bintray.com/signup/oss)，一定要选择这个注册链接，因为这个注册链接是面向个人的，是免费的，如果选择了公司版是需要收费的。注册的过程就很简单了，我们也可以通过github进行第三方登录。



### 2. 在bintray新建一个项目



![](http://upload-images.jianshu.io/upload_images/2585384-a5161d9e13cf3f53.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![](http://upload-images.jianshu.io/upload_images/2585384-dcf3a947ddc635ec.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



按照上述两幅图，填好项目描述等内容之后，点击Create就可以了。



### 3. 查看自己的key



![](http://upload-images.jianshu.io/upload_images/2585384-18643fd9ba680211.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 4. 在项目中配置上传所需的内容



首先修改项目的gradle(Project)

```java
buildscript {

    repositories {
        mavenCentral()
        jcenter()

    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.3.0'
        classpath 'com.github.dcendents:android-maven-plugin:1.2'
        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
          
        //新增内容
        classpath 'com.novoda:bintray-release:0.3.4'
        //==========新增结束==========
    }
}

allprojects {
    repositories {
        jcenter()
    }
	//新增内容，防止一些注释在编译过程报错
    tasks.withType(Javadoc) {
        options{
            encoding "UTF-8"
            charSet 'UTF-8'
            links "http://docs.oracle.com/javase/7/docs/api"
        }
    }
  	//==========新增结束==========
}
```



修改想要上传的module的gradle(Moudle)



```java
apply plugin: 'com.android.library'
//新增内容
apply plugin: 'com.novoda.bintray-release'
//==========新增结束==========  

android {
    compileSdkVersion 25
    buildToolsVersion "25.0.2"

    sourceSets.main {
        jniLibs.srcDir 'jni'
        jni.srcDirs = [] //disable automatic ndk-build call
    }

    defaultConfig {
        minSdkVersion 14
        targetSdkVersion 25
        versionCode 1
        versionName "1.0.0"
        multiDexEnabled true

    }
    buildTypes {
        release {
            
        }

        debug {
          
        }

    }

    lintOptions {
        abortOnError false
    }
}

dependencies {
    provided 'com.squareup.okhttp3:okhttp:3.5.0'
   
}
//新增内容
publish {
    userOrg = 'linsir'//bintray.com用户名
    repoName = 'linlog'
    groupId = 'com.linsir'//jcenter上的路径
    artifactId = 'linlog'//项目名称
    publishVersion = '1.0.0'//版本号
    desc = 'An android sdk for easy to log and toast.'//描述
    website = 'https://github.com/linsir6/linLog'//网站,尽量采用同样的格式
}
//==========新增结束==========  
```



### 5. 执行上传命令

在androidstudio中的Terminal中，找到当前的路径，然后执行以下命令：

```java
./gradlew clean build bintrayUpload -PbintrayUser=linsir -PbintrayKey=XXX -PdryRun=false
```



上述命令有两个地方需要替换成自己的，``-PbintrayUser=linsir``这个里面的linsir需要替换成自己在bintray上面的用户名，``-PbintrayKey=XXX``这里面的XXX需要替换成我们在``3. 查看自己的key``这步获取到的key，然后按下回车执行命令，当看到build success就完成了。



### 6.add to jcenter

当以上步骤全部完成之后，我们就可以在网站项目的界面中看到了，然后点击Add to Jcenter，然后添加一段描述就可以了。

![](http://upload-images.jianshu.io/upload_images/2585384-e55d80a7a32b55f3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

大概就应该在红色的这个位置，然后就可以等待工作人员的审核了，大概两个小时左右，审核通过之后会有站内信，邮箱内也收到邮件的，然后就可以通过``compile 'com.linsir:linLog:1.0.0``这种形式引用了。



> 我自己也写了一个简单的这样的库，大家如果参考的话可以看一下，[代码地址](https://github.com/linsir6/linLog)。
