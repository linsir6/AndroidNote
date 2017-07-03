> AudioSource和VideoSource都是MediaSource的子类，它们同样是包裹在C++外的一层，它们的功能是承载一个或多个AudioTrack/VideoTrack。

```
//AudioSource完全继承了父类，并没有任何的重写
public class AudioSource extends MediaSource {
  public AudioSource(long nativeSource) {
    super(nativeSource);
  }
}
```

```
//同样是继承了父类的所有的方法，但是新增了一个方法是，适应外界输出的分辨率
public VideoSource(long nativeSource) {
    super(nativeSource);
  }

  /**
   * Calling this function will cause frames to be scaled down to the requested resolution. Also,
   * frames will be cropped to match the requested aspect ratio, and frames will be dropped to match
   * the requested fps. The requested aspect ratio is orientation agnostic and will be adjusted to
   * maintain the input orientation, so it doesn't matter if e.g. 1280x720 or 720x1280 is requested.
   */
  public void adaptOutputFormat(int width, int height, int fps) {
    nativeAdaptOutputFormat(nativeSource, width, height, fps);
  }

  private static native void nativeAdaptOutputFormat(
      long nativeSource, int width, int height, int fps);
```

