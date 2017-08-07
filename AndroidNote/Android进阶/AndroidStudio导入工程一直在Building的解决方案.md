# Android导入项目一直在Building的解决方案

这种问题的发生的场景，一般是因为项目中的gradle的版本，或者sdk的版本我们本地环境中没有，所以需要先下载，然后才能导入，但是下载起来又特别的慢，所以我们需要修改一下待导入项目中用的配置。

我们可以找一个，我们可以运行的项目，然后将这些配置替换掉。

1.修改待倒入项目的gradle版本

找到 ``项目名称/gradle/wrapper/gradle-wrapper.properties``
将 ``distributionUrl=...`` 这一行，修改成我们已知项目一样即可


2.修改 ``项目名称/app/build.gradle``
将 ``targetSdkVersion`` 和 ``buildToolsVersion``  和``compileSdkVersion``修改成和我们能跑起来项目一样就可以了。



