# PathMeasure

PathMeasure是一个测量Path的路径的一个方法，我们今天的demo就是要做这样一个小东西，它会反复测量，运动的路径，并且沿着路径运行。

效果图：

![](https://ws3.sinaimg.cn/large/006tNc79ly1fh3i8c4k9ag309q0gagp9.gif)

实现的具体思路，就是，采用一个循环，反复的调用画图的方法，然后每当满一周之后，清零，再重新开始，为什么能沿着切线运动呢，是调用了一个参数，动态测量这个tan值。

代码：

```
public class CustomView extends View {

    private float currentValue = 0;     // 用于纪录当前的位置,取值范围[0,1]映射Path的整个长度

    private float[] pos;                // 当前点的实际位置
    private float[] tan;                // 当前点的tangent值,用于计算图片所需旋转的角度
    private Bitmap mBitmap;             // 箭头图片
    private Matrix mMatrix;             // 矩阵,用于对图片进行一些操作

    private Paint mPaint;

    private int mViewWidth;
    private int mViewHeight;

    public CustomView(Context context) {
        this(context, null);
    }

    public CustomView(Context context, @Nullable AttributeSet attrs) {
        super(context, attrs);
        init(context);
        mPaint = new Paint();
        mPaint.setColor(Color.BLACK);
        mPaint.setStrokeWidth(8);
        mPaint.setStyle(Paint.Style.STROKE);
        mPaint.setTextSize(60);


    }

    private void init(Context context) {
        pos = new float[2];
        tan = new float[2];
        BitmapFactory.Options options = new BitmapFactory.Options();
        options.inSampleSize = 15;       // 缩放图片
        mBitmap = BitmapFactory.decodeResource(context.getResources(), R.drawable.arrowhead, options);
        mMatrix = new Matrix();
    }


    @Override
    protected void onSizeChanged(int w, int h, int oldw, int oldh) {
        super.onSizeChanged(w, h, oldw, oldh);
        mViewHeight = h;
        mViewWidth = w;

    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        canvas.translate(mViewWidth / 2, mViewHeight / 2);      // 平移坐标系

        Path path = new Path();                                 // 创建 Path

        path.addCircle(0, 0, 200, Path.Direction.CW);           // 添加一个圆形

        PathMeasure measure = new PathMeasure(path, false);     // 创建 PathMeasure

        currentValue += 0.005;                                  // 计算当前的位置在总长度上的比例[0,1]
        if (currentValue >= 1) {
            currentValue = 0;
        }

        measure.getPosTan(measure.getLength() * currentValue, pos, tan);        // 获取当前位置的坐标以及趋势

        mMatrix.reset();                                                        // 重置Matrix
        float degrees = (float) (Math.atan2(tan[1], tan[0]) * 180.0 / Math.PI); // 计算图片旋转角度

        mMatrix.postRotate(degrees, mBitmap.getWidth() / 2, mBitmap.getHeight() / 2);   // 旋转图片
        mMatrix.postTranslate(pos[0] - mBitmap.getWidth() / 2, pos[1] - mBitmap.getHeight() / 2);   // 将图片绘制中心调整到与当前点重合

        canvas.drawPath(path, mPaint);                                   // 绘制 Path
        canvas.drawBitmap(mBitmap, mMatrix, mPaint);                     // 绘制箭头

        invalidate();
    }

}

```

代码地址：https://github.com/linsir6/mCustomView/tree/master/TestPathMeasure