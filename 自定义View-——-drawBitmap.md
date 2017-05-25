# 自定义View —— drawBitmap

> 最近在复习自定义view，学习了GitHub上面有一个非常详细的自定义view的教程，就打算跟着把里面的demo都做一遍，然后记录一下学习到的checkView。[教程地址](http://www.gcssloop.com/customview/CustomViewIndex)



![效果图](http://upload-images.jianshu.io/upload_images/2585384-8f6561376acf91b7.gif?imageMogr2/auto-orient/strip)


``drawBitmap``是指将一张图片一张图片画在画布上面。这里面调用的：

```
public void drawBitmap(Bitmap bitmap, Rect src, Rect dst, Paint paint) {}
```

参数的含义就很好理解了：
bitmap：画什么图片
src：要画图片中的哪个部分
dst：要把图片画到画布中的哪个位置
paint：画笔

我们这里需要的一个长图：

![](http://upload-images.jianshu.io/upload_images/2585384-e55222c86cd8af0c.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这个drawBitmap方法是可以重复使用的，可以多次画，然后画出来的效果会叠加在一起，那么我们便可以第一次画一个非常小的对号的一部分，然后一点一点地多，最后就成为一个动态的效果了，我们事分成了13次画的，通过的事handler来控制实现的。


核心代码：


```java

mHandler = new Handler() {

            @Override public void handleMessage(Message msg) {
                super.handleMessage(msg);
                //确定当前没有view
                if (animCurrentPage < animMaxPage && animCurrentPage >= 0) {
                    //画一下
                    invalidate();
                    if (animState == ANIM_NULL) {
                        return;
                    }
                    //判断当前是要画对号，然后每次动态移动一点
                    if (animState == ANIM_CHECK) {
                        animCurrentPage++;
                    } else if (animState == ANIM_UNCHECK) {
                        animCurrentPage--;
                    }

                    // 延时发送消息，然后自己接收，形成了一个循环
                    this.sendEmptyMessageDelayed(0, animDuration / animMaxPage);


                } else {
                    //不需要画了，恢复到默认值
                    if (isCheck) {
                        animCurrentPage = animMaxPage - 1;
                    } else {
                        animCurrentPage = -1;
                    }

                    invalidate();
                    animState = ANIM_NULL;
                }
            }
        };

```


```java

@Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        //将画笔移到view的中央
        canvas.translate(mWidth / 2, mHeight / 2);
        //画一个圆
        canvas.drawCircle(0, 0, 240, mPaint);

        //找到高度
        int sideLength = okBitmap.getHeight();
        
        //控制画出图片上面的哪一个部分
        Rect src = new Rect(sideLength * animCurrentPage, 0, sideLength * (animCurrentPage + 1), sideLength);
        
        //画在画布上面的哪个位置
        Rect dst = new Rect(-200, -200, 200, 200);

        //画
        canvas.drawBitmap(okBitmap, src, dst, null);
    }

```


```java

public void check() {
        //触发想要绘画的方法
        if (animState != ANIM_NULL || isCheck) {
            return;
        }
        animState = ANIM_CHECK;
        animCurrentPage = 0;
        mHandler.sendEmptyMessageDelayed(0, animDuration / animMaxPage);
        isCheck = true;
    }
```


----

到这里一个简单的自定义view就已经实现咯～


[源码地址](https://github.com/linsir6/mCustomView/tree/master/CheckView)：https://github.com/linsir6/mCustomView/tree/master/CheckView
