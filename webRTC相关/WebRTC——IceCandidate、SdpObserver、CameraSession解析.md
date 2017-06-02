> IceCandidate是一个模板类，里面主要包含着会话描述协议。

```
public class IceCandidate {
  public final String sdpMid;//描述协议的id
  public final int sdpMLineIndex;//描述协议的行索引
  public final String sdp;//会话描述协议

  public IceCandidate(String sdpMid, int sdpMLineIndex, String sdp) {
    this.sdpMid = sdpMid;
    this.sdpMLineIndex = sdpMLineIndex;
    this.sdp = sdp;
  }

  public String toString() {
    return sdpMid + ":" + sdpMLineIndex + ":" + sdp;
  }
}
```

----

> SdpObserver是来回调sdp是否创建(offer,answer)成功，是否设置描述成功(local,remote）的一个接口。

```
 /** Called on success of Create{Offer,Answer}(). */
  public void onCreateSuccess(SessionDescription sdp);

  /** Called on success of Set{Local,Remote}Description(). */
  public void onSetSuccess();

  /** Called on error of Create{Offer,Answer}(). */
  public void onCreateFailure(String error);

  /** Called on error of Set{Local,Remote}Description(). */
  public void onSetFailure(String error);
```
----

> CameraSession是用来回调相机信息的一个接口

```
public interface CreateSessionCallback {//创建相机描述的回调
    void onDone(CameraSession session);//成功
    void onFailure(String error);//不成功
  }
```

```
public interface Events {
    void onCameraOpening();//当相机打开
    void onCameraError(CameraSession session, String error);//相机发生故障
    void onCameraDisconnected(CameraSession session);//断开连接
    void onCameraClosed(CameraSession session);//关闭
    void onByteBufferFrameCaptured(
        CameraSession session, byte[] data, int width, int height, int rotation, long timestamp);
    void onTextureFrameCaptured(CameraSession session, int width, int height, int oesTextureId,
        float[] transformMatrix, int rotation, long timestamp);
  }
```

```
void stop();//回调到相机停止工作
```
----




