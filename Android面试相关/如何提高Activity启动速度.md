　　
# 如何提高Activity启动速度

 减少onCreate的时间，那就精简onCreate里的代码。放在onResume里好了。为了用户体验更好一些，把页面显示的View细分一下，放在AsyncTask里逐步显示，如果你够熟练，用handler更好，这样用户的看到的就是有层次有步骤的一个个的view的展示，不会是先看到一个黑屏，然后一下显示所有view。最好作成动画，效果更自然些。利用多线程的目的就是尽可能的减少onCreate和onReume的时间，使得用户能尽快看到页面，操作页面。
　　

 但是，很多操作是只需要一次初始化的，都放在onResume里每次进入activity都会浪费初始化时间。这个好解决，做一个boolean变量，在onCreate里标记为true。在onResume里判断为true就进行初始化，初始化完成立刻置为false。搞定。


1.减小主线程的阻塞时间　

   　若一个操作耗时教长(超过5秒 用户无响应5秒 网络和数据库阻塞10秒 广播接收者执行超过10秒会导致ANR),我们应该将其放入后台线程中执行,只在需要修改UI界面时通知主线程进行修改。
    Android已经提供了AsynTask以实现从主线程生成新的异步任务的方法。具体用法参见异步任务。　
    
2.提高Adapter和AdapterView的效率
    (1)重用已生成过的Item View
    (2) 添加ViewHolder
    (3) 缓存Item的数据
    (4)分段显示　
    
3.优化布局文件
   如果我们的布局层次过多,那么在我们用findViewById的时间必然会变多，一个变多可能不要紧，但是有很多调用必然会影响性能。

   (1) 使用观察布局的工具 Hierarchy Viewer

   (2)使用布局优化工具: Layoutopt

   (3)优化布局的层次结构

