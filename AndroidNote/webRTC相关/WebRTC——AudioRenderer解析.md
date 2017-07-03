> AudioRenderer是Audio的渲染类，负责音频的渲染

```
public static class AudioFrame {
        public byte[] audio_data;    //音频数据
        public int bits_per_sample;    //bit音频的示例
        public int sample_rate;    //示例比特率
        public int number_of_channels;     //声道的数量
        public int number_of_frames;    //帧的数量

         //构造方法
        public AudioFrame(byte[] audio_data, int bits_per_sample, int sample_rate, int number_of_channels, int number_of_frames) {
            this.audio_data = audio_data;
            this.sample_rate = sample_rate;
            this.bits_per_sample = bits_per_sample;
            this.number_of_channels = number_of_channels;
            this.number_of_frames = number_of_frames;
        }
    }
```

```
//回调接口，当有音频帧的时候产生回调用的
public static interface Callbacks {
        public void onAudioFrame(AudioFrame frame);
    }
```

```
long nativeAudioRenderer;
//创建AudioRenderer
public AudioRenderer(Callbacks callbacks) {
    nativeAudioRenderer = nativeWrapAudioRenderer(callbacks);
}
private static native long nativeWrapAudioRenderer(Callbacks callbacks);

```

```
/销毁掉audioRenderer
public void dispose() {
        if (nativeAudioRenderer == 0) {
            return;
        }
        // todo  free native audio renderer
        nativeAudioRenderer = 0;
    }
```









