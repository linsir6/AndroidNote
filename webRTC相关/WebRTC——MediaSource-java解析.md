> MediaSource是AudioSource和VideoSource的基类，它里面定义了一些方法，供子类继承。
它是一层包裹在C++外面的一层，C++里面也是有MediaSource的。

```
  //一个媒体资源类具有以下四个状态，初始化中，工作中，结束，消音/消去视频  
  public enum State { INITIALIZING, LIVE, ENDED, MUTED }
```

```
  创建时需要传进来一个nativeSource
  final long nativeSource; // Package-protected for PeerConnectionFactory.

  public MediaSource(long nativeSource) {
    this.nativeSource = nativeSource;
  }
```

```
  //获取当前的状态，通过调用native层方法获取到
  public State state() {
    return nativeState(nativeSource);
  }
```

```
  //销毁当前的媒体资源
  public void dispose() {
    free(nativeSource);
  }
```

```
  //两个native层的方法，用来获取状态和释放资源的
  private static native State nativeState(long pointer);

  private static native void free(long nativeSource);
```
