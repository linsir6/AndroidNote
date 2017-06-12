# 记录一些mac上面常用的命令

- 查看端口占用情况: ``lsof -i:5001``
- kill掉进程: `` kill 6327``

- 查看/取消查看 隐藏文件命令
OS X（10.6~10.8 :
``defaults write com.apple.Finder AppleShowAllFiles Yes && killall Finder ``//显示隐藏文件
defaults write com.apple.Finder AppleShowAllFiles No && killall Finder //不显示隐藏文件
3
当升级到OS X 10.9 Mavericks版本之后，这两条命令需要做一些修改，变成了如下命令：
defaults write com.apple.finder AppleShowAllFiles Yes && killall Finder //显示隐藏文件
defaults write com.apple.finder AppleShowAllFiles No && killall Finder //不显示隐藏文件