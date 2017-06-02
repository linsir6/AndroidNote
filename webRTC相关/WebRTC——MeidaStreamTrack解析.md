> MeidaStreamTrack是媒体流的一部分

```
  //它的两种状态分别是工作状态和结束状态
  public enum State { LIVE, ENDED }
```

```
  // 构造方法，在创建MediaStream的时候，需要传入一个nativeTrack
  final long nativeTrack;

  public MediaStreamTrack(long nativeTrack) {
    this.nativeTrack = nativeTrack;
  }
```

```
  //这里面的方法和native层的方法是一一对应的
  //获取Id  
  public String id() {
    return nativeId(nativeTrack);
  }
  
  //获取类别
  public String kind() {
    return nativeKind(nativeTrack);
  }

  //获取是否被mute 
  public boolean enabled() {
    return nativeEnabled(nativeTrack);
  }

  //mute或者取消
  public boolean setEnabled(boolean enable) {
    return nativeSetEnabled(nativeTrack, enable);
  }

  //获取当前的状态
  public State state() {
    return nativeState(nativeTrack);
  }

  //释放掉
  public void dispose() {
    free(nativeTrack);
  }

  private static native String nativeId(long nativeTrack);

  private static native String nativeKind(long nativeTrack);

  private static native boolean nativeEnabled(long nativeTrack);

  private static native boolean nativeSetEnabled(long nativeTrack, boolean enabled);

  private static native State nativeState(long nativeTrack);

  private static native void free(long nativeTrack);

```
