# 动态申请权限库：easypermissions使用与源码解析

当接触了Android 6.0 7.0 之后，很多人就会发现，单纯的在AndroidManifest.xml中声明权限已经是不好使的了，因为Google为了保护用户的权限，需要应用动态的权限申请。

下面我们就介绍一个Google官方放出来的动态申请权限的库，[GitHub地址](https://github.com/googlesamples/easypermissions)，这个库可以简单的帮助我们完成动态申请权限的整个流程，并且可以将结果回调回来，因此我们可以在回调结果中加上我们的处理逻辑。

## Installation 安装

EasyPermissions is installed by adding the following dependency to your build.gradle file:

```java
dependencies {
    compile 'pub.devrel:easypermissions:0.4.0'
}
```


## Usage 用法

### Basic 基础

To begin using EasyPermissions, have your Activity (or Fragment) override the onRequestPermissionsResult method:

开始用这个库的时候，需要让Activity或者Fragment重写onRequestPermissionsResult这个方法：

```
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);

        // Forward results to EasyPermissions
        // 远期回调回来的结果
        EasyPermissions.onRequestPermissionsResult(requestCode, permissions, grantResults, this);
    }
}
```

## Request Permissions
The example below shows how to request permissions for a method that requires both CAMERA and ACCESS_FINE_LOCATION permissions. There are a few things to note:

- Using EasyPermissions#hasPermissions(...) to check if the app already has the required permissions. This method can take any number of permissions as its final argument.

- Requesting permissions with EasyPermissions#requestPermissions. This method will request the system permissions and show the rationale string provided if necessary. The request code provided should be unique to this request, and the method can take any number of permissions as its final argument.

- Use of the AfterPermissionGranted annotation. This is optional, but provided for convenience. If all of the permissions in a given request are granted, any methods annotated with the proper request code will be executed. This is to simplify the common flow of needing to run the requesting method after all of its permissions have been granted. This can also be achieved by adding logic on the onPermissionsGranted callback.

下面这个例子展示了如何申请权限用一个方法同时申请相机和申请定位的权限，这里有一些内容需要注意：

- 用EasyPermissions的hasPermissions方法检测一下，是否app已经具有要申请的权限。这个方法可以将许多方法作为最后的论证。

- 申请权限通过EasyPermissions的requestPermissions的方法。这个方法将会申请系统的权限，并且在如果有必要的条件下会展示出理由。这个申请权限的代码应该提供独一无二的申请，并且这些方法可以提供很多权限作为最终的定论。

//todo








