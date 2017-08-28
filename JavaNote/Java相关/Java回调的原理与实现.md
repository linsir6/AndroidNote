> 回调原本应该是一个非常简单的概念，但是可能因为平时只用系统为我们写好的回调的接口了，自己很少实现回调，所以在自己实现回调的时候还是有一点点晕的，现在写这篇文章记录一下，也和大家分享一下怎么写回调接口。

##回调
回调的概念：举个例子就是，我们想要问别人一道题，我们把题跟对方说了一下，对方说好，等我做完这道题，我就告诉你，这个时候就用到了回调，因为我们并不知道对方什么时候会做完，而是对方做完了来主动找我们。
  ####同步回调
  代码运行到某一个位置的时候，如果遇到了需要回调的代码，会在这里等待，等待回调结果返回后再继续执行。
  ####异步回调
代码执行到需要回调的代码的时候，并不会停下来，而是继续执行，当然可能过一会回调的结果会返回回来。


----
###具体代码：

[代码链接](https://github.com/linsir6/TestCallback)

总体的代码还是很简单的，就是模拟了一个打印机，还有一个人，打印机具有打印的功能，但是打印需要时间，不能在收到任务的同时给出反馈，需要等待一段时间才能给出反馈。这个人想做的就是打印一份简历，然后知道打印的结果。这里面代码实现了这两种方式。

````
Callback.java

public interface Callback {
	void printFinished(String msg);
}

````

````
Printer.java

public class Printer {
	public void print(Callback callback, String text) {
		System.out.println("正在打印 . . . ");
		try {
			Thread.currentThread();
			Thread.sleep(3000);// 毫秒
		} catch (Exception e) {
		}
		callback.printFinished("打印完成");
	}
}
````

````
People.java

public class People {

	Printer printer = new Printer();

	/*
	 * 同步回调
	 */
	public void goToPrintSyn(Callback callback, String text) {
		printer.print(callback, text);
	}

	/*
	 * 异步回调
	 */
	public void goToPrintASyn(Callback callback, String text) {
		new Thread(new Runnable() {
			public void run() {
				printer.print(callback, text);
			}
		}).start();
	}
}
````

````
Main.java

public class Main {//测试类，同步回调
	public static void main(String[] args) {
		People people = new People();
		Callback callback = new Callback() {
			@Override
			public void printFinished(String msg) {
				System.out.println("打印机告诉我的消息是 ---> " + msg);
			}
		};
		System.out.println("需要打印的内容是 ---> " + "打印一份简历");
		people.goToPrintSyn(callback, "打印一份简历");
		System.out.println("我在等待 打印机 给我反馈");
	}
}
````


![同步回调](http://upload-images.jianshu.io/upload_images/2585384-38d968042a37386f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


````
Main.java

public class Main {//异步回调
	public static void main(String[] args) {
		People people = new People();
		Callback callback = new Callback() {
			@Override
			public void printFinished(String msg) {
				System.out.println("打印机告诉我的消息是 ---> " + msg);
			}
		};
		System.out.println("需要打印的内容是 ---> " + "打印一份简历");
		people.goToPrintASyn(callback, "打印一份简历");
		System.out.println("我在等待 打印机 给我反馈");
	}
}
````


![异步回调](http://upload-images.jianshu.io/upload_images/2585384-2b0788ad5d711c05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
