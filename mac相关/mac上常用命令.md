# 记录一些mac上面常用的命令

- 查看端口占用情况: ``lsof -i:5001``

- kill掉进程: `` kill -15/-9 6327``

- 查看/取消 隐藏文件命令

    OS X（10.6~10.8) :
    ``defaults write com.apple.Finder AppleShowAllFiles Yes && killall Finder``//显示隐藏文件

    ``defaults write com.apple.Finder AppleShowAllFiles No && killall Finder`` //不显示隐藏文件

    OS X 10.9+ :
    ``defaults write com.apple.finder AppleShowAllFiles Yes && killall Finder`` //显示隐藏文件

    ``defaults write com.apple.finder AppleShowAllFiles No && killall Finder`` //不显示隐藏文件

- 根绝关键字查询占用情况: ``ps -ef|grep gradle``

- 根绝关键字查询占用情况2: ``netstat -an|grep 8080``

- 查看iterm2的配置: ``nano .zshrc`` 两个我比较喜欢的主题:1.jonathan  2.robbyrussell





