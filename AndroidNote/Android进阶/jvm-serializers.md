# Jvm-serializers


# Home

Pascal S. de Kloe edited this page on 9 Jul 2016 · 68 revisions


# 测试平台

OS:Mac OS X
JVM:Oracle Corporation 1.8.0_91
CPU:2.8 GHz Intel Core i7 os-arch:Darwin Kernel Version 15.5.0
Cores (incl HT):8


# 公开声明

这个测试关注点在于对于一个循环的结构体的编码和解码，但是不同特征集对于不同的算法有着不一样的结果：

- 一些序列化支持循环侦查，分享其它正好写非循环树结构
- 一些包含充满元数据在序列化的过程中，一些不能
- 一些是跨平台的，一些是语言特有的
- 一些是以文字为基础的，一些是以二进制为基础的
- 一些提供了版本向前/向后兼容，但是有的没有提供


不同的数据将会产生不同的结果(例如添加一个非ascii的字符到每一个字符串，然而将会给出一个未加工的关于库的性能








































