# Android报错:Manifest merger failed with multiple errors, see logs

在编写Android代码的时候可能会遇到这样的错误：``Manifest merger failed with multiple errors, see logs``，但是遇到这样的问题，我们的内心是崩溃的，因为它告诉我们，我们的代码有问题，编译过过去，但是又没有告诉我们问题在哪里，所以我们需要自己找问题。



在Android studio自带的命令行里面，我们输入：``gradlew processDebugManifest —stacktrace``



这样我们就能获得更多的信息，我们便可以根据信息进行处理了。



常遇到这样问题的场景，一般都是，在自己的项目中引用到了，第三方的库，但是我们的最低版本的要求和库的版本要求可能不太一样，这个时候两个.gradle的文件在merage的时候就会产生冲突，就会报错了，我们只需要将他们两个改成一样的就可以。



一般来说遇到这种问题的大多数的场景，都是多个.gradle文件在合并的过程中遇到了问题，我们可以根据报错，和我们的回忆来检查到底是哪里出现的问题。
