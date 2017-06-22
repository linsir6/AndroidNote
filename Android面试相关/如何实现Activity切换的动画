 **android中设置activity切换动画有 两种实现方式**
 
 1 . 在 AndroidManifest.xml 文件activity标签中，通过设置 android:theme 主题属性来自定义我们 Activity的切换动画( 主题可以定义很多属性，动画只是其中之一)。
 

```
<activity
    android:name="whateverNameActivity"
    android:theme="@style/myActivityTheme" >
</activity>
```

首先要定义自己的主题，打开res/values/styles.xml文件，加入

```
<style name="myActivityTheme">
  <itemname="android:windowAnimationStyle">@style/myAnimTheme />
</style>
```
然后继续定义具体切换动画样式，分为4种需要动画的情况。

打开新界面时 ：
					

 - 新界面出现（android:activityOpenEnterAnimation）
 - 当前界面消失（android:activityOpenExitAnimation）

返回上一界面时：

 - 当前界面消失（android:activityCloseExitAnimation）
 - 上一界面出现（android:activityCloseEnterAnimation）

> a、b、c、d为自定义在res/anim下的具体动画效果文件（下面贴出）

```
<style name="myAnimTheme " parent="@android:style/Animation.Activity">
    <item name="android:activityOpenEnterAnimation">@anim/a />
    <item name="android:activityOpenExitAnimation">@anim/b />
    <item name="android:activityCloseEnterAnimation">@anim/c />
    <item name="android:activityCloseExitAnimation">@anim/d />
</style>
```

2 . 在Android的2.0版本之后，加入了overridePendingTransition（）这个函数来帮我们实现activity切换动画，它**在startActivity()或者finish()函数之后调用**

![这里写图片描述](http://img.blog.csdn.net/20160408111715900)

它有两个参数，
enterAnim是下一界面进入效果的xml文件的id, 
exitAnim是当前界面退出效果的xml文件id。

> 我们可以看出它也实现了第一种方式的四种动画情况。

注意： 

 - 当我们不想要动画时，设置为 0 即可。
 - 我们可以看出这个方法是定义在android.app.Activity下的，如果我们用自定义的view或fragment等嵌入到Activity中，调用这个函数时很可能不起作用。一般改写为this.getParent().overridePendingTransition 就可以解决。

3 .上 res/anim 下的各种动画文件

zoomin.xml: 

```
<?xml version="1.0" encoding="utf-8"?> 
<set xmlns:android="http://schemas.android.com/apk/res/android" 
android:interpolator="@android:anim/decelerate_interpolator"> 

<scale android:fromXScale="0.1" 
android:toXScale="1.0" 
android:fromYScale="0.1" 
android:toYScale="1.0" 
android:pivotX="50%p" 
android:pivotY="50%p" 
android:duration="300" /> 

<alpha 
android:fromAlpha="0.1" 
android:toAlpha="1.0" 
android:duration="300" /> 
</set> 
```
zoomout.xml 

```
<?xml version="1.0" encoding="utf-8"?> 
<set xmlns:android="http://schemas.android.com/apk/res/android" 
android:interpolator="@android:anim/decelerate_interpolator" 
android:zAdjustment="top"> 

<scale android:fromXScale="1.0" 
android:toXScale=".5" 
android:fromYScale="1.0" 
android:toYScale=".5" 
android:pivotX="50%p" 
android:pivotY="50%p" 
android:duration="300" /> 

<alpha android:fromAlpha="1.0" 
android:toAlpha="0" 
android:duration="300"/> 
</set> 
```
out_from_right.xml

```
<?xml version="1.0" encoding="utf-8"?>

<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="500"
    android:fromXDelta="0"
    android:fromYDelta="0"
    android:toXDelta="100%p"
    android:toYDelta="0" >

</translate>
```

in_from_left.xml

```
<?xml version="1.0" encoding="utf-8"?>

<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="500"
    android:fromXDelta="-100%p"
    android:fromYDelta="0"
    android:toXDelta="0"
    android:toYDelta="0" >

</translate>
```
out_from_left.xml

```
<?xml version="1.0" encoding="utf-8"?>

<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="500"
    android:fromXDelta="0"
    android:fromYDelta="0"
    android:toXDelta="-100%p"
    android:toYDelta="0" >

</translate>
```

in_from_right.xml

```
<?xml version="1.0" encoding="utf-8"?>
<translate xmlns:android="http://schemas.android.com/apk/res/android"
    android:duration="500"
    android:fromXDelta="100%p"
    android:fromYDelta="0"
    android:toXDelta="0"
    android:toYDelta="0" >

</translate>
```
fade.xml

```
<?xml version="1.0" encoding="utf-8"?>

<alpha xmlns:android="http://schemas.android.com/apk/res/android"
       android:interpolator="@android:anim/accelerate_interpolator"
       android:fromAlpha="0.0" android:toAlpha="1.0"
       android:duration="2000" />

```

hold.xml

```
<?xml version="1.0" encoding="utf-8"?>

<translate xmlns:android="http://schemas.android.com/apk/res/android"
       android:interpolator="@android:anim/accelerate_interpolator"
       android:fromXDelta="0" android:toXDelta="0"
       android:duration="2000" />

```
hyperspace_in.xml

```
<?xml version="1.0" encoding="utf-8"?>

<alpha xmlns:android="http://schemas.android.com/apk/res/android" 
android:fromAlpha="0.0" 
android:toAlpha="1.0" 
android:duration="2000" 
android:startOffset="1200" />

```

hyperspace_out.xml

```
<?xml version="1.0" encoding="utf-8"?>


<set xmlns:android="http://schemas.android.com/apk/res/android"
	android:shareInterpolator="false">
	<scale android:interpolator="@android:anim/accelerate_decelerate_interpolator"
		android:fromXScale="1.0" 
		android:fromYScale="1.0"
		android:toYScale="0.6" 
		android:pivotX="50%" 
		android:pivotY="50%"
        android:duration="2000" />
        
	<set android:interpolator="@android:anim/accelerate_interpolator"
		android:startOffset="700">
		<scale android:fromXScale="1.4"
		 android:toXScale="0.0"
		android:toYScale="0.0"
		android:pivotX="50%"
		android:pivotY="50%" 
		android:duration="2000" />
		<rotate android:fromDegrees="0" 
		android:toDegrees="-45"
		android:pivotX="50%" 
		android:pivotY="50%"
		android:duration="2000" />
	</set>
</set>


``` 
alpha_action.xml

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android" >
<alpha android:fromAlpha="1.0" 
android:toAlpha="0" 
android:duration="2000"/> 
<!-- 透明度控制动画效果 alpha
        0.0表示完全透明
        1.0表示完全不透明
        以上值取0.0-1.0之间的float数据类型的数字
        
        
-->
</set>
``` 
scale_action.xml

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
	<scale android:interpolator="@android:anim/accelerate_decelerate_interpolator"
		android:fromXScale="0.0" 
		android:toXScale="1.4" 
		android:fromYScale="0.0"
		android:toYScale="1.4" 
		android:pivotX="50%" 
		android:pivotY="50%"
		android:fillAfter="false" 
		android:duration="2000" />
</set>
``` 

scale_rotate.xml

```
<?xml version="1.0" encoding="utf-8"?>
<!-- android:duration="@android:integer/config_mediumAnimTime" -->
<set xmlns:android="http://schemas.android.com/apk/res/android"
	android:shareInterpolator="false">
	<scale android:interpolator="@android:res/anim/accelerate_decelerate_interpolator"
		android:fromXScale="0.0" 
		android:toXScale="1.0" 
		android:fromYScale="0.0"
		android:toYScale="1.0" 
		android:pivotX="50%" 
		android:pivotY="50%"
		android:duration="2000" 
		android:repeatCount="0" 
		android:startOffset="20"></scale>
		
	<rotate android:interpolator="@android:anim/accelerate_decelerate_interpolator"
		android:fromDegrees="0" 
		android:toDegrees="+355" 
		android:pivotX="50%"
		android:pivotY="50%" 
		android:duration="2000" />
</set>

``` 

scale_translate.xml

```
<?xml version="1.0" encoding="utf-8"?>
<!-- android:duration="@android:integer/config_mediumAnimTime" -->
<set xmlns:android="http://schemas.android.com/apk/res/android"
	android:shareInterpolator="false">
	<scale android:interpolator="@android:res/anim/accelerate_decelerate_interpolator"
		android:fromXScale="0.0" 
		android:toXScale="1.0" 
		android:fromYScale="0.0"
		android:toYScale="1.0" 
		android:pivotX="0" 
		android:pivotY="0"
		android:duration="2000" 
		android:repeatCount="0" 
		android:startOffset="0"></scale>
		
	<translate android:fromXDelta="0" 
		android:toXDelta="0"
		android:fromYDelta="0" 
		android:toYDelta="0" 
		android:duration="2000" />
</set>

``` 
scale_translate_rotate.xml

```
<?xml version="1.0" encoding="utf-8"?>
<!-- android:duration="@android:integer/config_mediumAnimTime" -->
<set xmlns:android="http://schemas.android.com/apk/res/android"
	android:shareInterpolator="false">
	<scale android:interpolator="@android:res/anim/accelerate_decelerate_interpolator"
		android:fromXScale="0.0" 
		android:toXScale="1.0" 
		android:fromYScale="0.0"
		android:toYScale="1.0"
		android:pivotX="50%" 
		android:pivotY="50%"
		android:duration="2000"></scale>
		
	<translate android:interpolator="@android:anim/accelerate_decelerate_interpolator"
		android:fromXDelta="120"
		android:toXDelta="30" 
		android:fromYDelta="30"
		android:toYDelta="250" 
		android:duration="2000" />
		
	<rotate android:interpolator="@android:anim/accelerate_decelerate_interpolator"
		android:fromDegrees="0" 
		android:toDegrees="+355" 
		android:pivotX="50%"
		android:pivotY="50%"
		android:duration="2000" />
</set>

``` 

slide_down_out.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<set android:interpolator="@android:anim/accelerate_interpolator"
	xmlns:android="http://schemas.android.com/apk/res/android">
	<translate android:duration="2000"
		android:fromYDelta="0.0"
		android:toYDelta="100.0%p" />
</set>
``` 

wave_scale.xml

```
<?xml version="1.0" encoding="utf-8"?>

<set xmlns:android="http://schemas.android.com/apk/res/android"
	android:interpolator="@android:anim/accelerate_interpolator">
	<alpha android:fromAlpha="0.0" 
		android:toAlpha="1.0"
		android:duration="2000" />
		
	<scale android:fromXScale="0.5" 
		android:toXScale="1.5"
		android:fromYScale="0.5" 
		android:toYScale="1.5" 
		android:pivotX="50%"
		android:pivotY="50%" 
		android:duration="2000" />
		
	<scale android:fromXScale="1.5" 
		android:toXScale="1.0"
		android:fromYScale="1.5" 
		android:toYScale="1.0" 
		android:pivotX="50%"
		android:pivotY="50%" 
		android:startOffset="200"
		android:duration="2000" />
</set>

```