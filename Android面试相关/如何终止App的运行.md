# 如何终止App的运行

- 在application中定义一个单例模式的Activity栈来管理所有Activity。并提供退出所有Activity的方法。


- AndroidManifest.xml 添加权限

``<uses-permission android:name="android.permission.KILL_BACKGROUND_PROCESSES" />``

退出应用的方法：


```
ActivityManager am= (ActivityManager) this
		.getSystemService(Context.ACTIVITY_SERVICE);
am.killBackgroundProcesses(this.getPackageName());
```

- Dalvik VM的本地方法
  android.os.Process.killProcess(android.os.Process.myPid())    //获取PID 
  System.exit(0);   //常规java、c#的标准退出法，返回值为0代表正常退出

-Android的窗口类提供了历史栈

我们可以通过stack的原理来巧妙的实现，这里我们在A窗口打开B窗口时在Intent中直接加入标 志  Intent.FLAG_ACTIVITY_CLEAR_TOP，这样开启B时将会清除该进程空间的所有Activity。
在A窗口中使用下面的代码调用B窗口

```
Intent intent = new Intent(); 
intent.setClass(this, B.class); 
intent.setFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP);  //注意本行的FLAG设置 
startActivity(intent);
```

接下来在B窗口中需要退出时直接使用finish方法即可全部退出。