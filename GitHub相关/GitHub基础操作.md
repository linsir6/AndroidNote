> 虽然以前也有一些git的基础，但是好久不用了，基本也都忘没了，而且以前用图形化界面的工具比较多，最近决定多用用命令行吧，感觉命令行还是挺好用的。

最近在mac上面装了iterm2感觉挺好用的，还支持各种扩展，挺好的。[iterm2下载链接](http://www.iterm2.com/)

----
就不做什么过多的介绍了，github也这么多年了，还是不错的，而且今天打算记录的也是git的命令，等以后会用到更多的命令的时候也会更新这篇博客的。

----

| 命令        | 含义           |
| ------------- |:-------------:|
|git branch      | 查看本地所有分支  |
|git status       |查看当前状态          | 
|git commit     | 提交                        |
|git branch -a |查看所有的分支       |
|git branch -r  |查看远程所有分支   |
|git commit -m "注释"| 提交并加注释|
|git push origin master|将分支推送到服务器上|
|git remote show origin|显示远程库里面的资源|
|git remote -v|查看远程仓库|
|git checkout dev|建立一个新的本地分支|
|git merge origin/dev|将分支dev与当前分支进行合并|
|git checkout dev|切换到本地dev分支|
|git remote show|查看远程库|
|git add .|将修改全部添加进去|
|git rm 文件名|删除指定文件|
|git pull|将本地代码与服务器同步|
|git push origin master|将本地项目提交到服务器中|
|git clone|将代码克隆到本地|
|git checkout [name]|切换分支|
|git push origin --delete [name]|删除远程分支|
----

![github](http://upload-images.jianshu.io/upload_images/2585384-2a10c46f536c94a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
以上就是总结给自己看的吧，如果大家有什么疑问也可以留言问，我有空也会介绍一下原理和与其它版本控制工具的对比


较为简单的上传本地代码到GitHub：
````
git init
git remote add [shortname] [url]
git pull origin master
git add .
git commit -m "description"
git push origin master
````

```
修改本地用户

git config --global user.name "youname"
git config --global user.email "youeamil@email.com"
```


