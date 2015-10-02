title: Xcode6出现多个模拟器 显示的都是UUID 没有版本号
date: 2015-09-26 10:33:22
tags:
---
## Xcode6出现多个模拟器 显示的都是UUID 没有版本号
pro 装了 Xcode 6,7. 后面打开Xcode6 出现好多重复的模拟器, 而且显示的都是UUID 没有版本号,看着特别不爽.
本来是打开Device,准备一个一个删除模拟器的,看到太多了,好麻烦.
<br>google之后[在这里](http://www.oschina.net/code/snippet_196012_50574)看到
<br><pre>1.关闭xcode
2.终端输入 sudo killall -9 com.apple.CoreSimulator.CoreSimulatorService 输入你的电脑密码
3.终端输入 rm -rf ~/Library/Developer/CoreSimulator/Devices
</pre>
###第一步可以省略.操作之后发现问题解决了.然后再Device或者按住 `cmd+shift+2`添加新的模拟器即可.
![](http://ww3.sinaimg.cn/large/773d7193gw1ewfnmrnyvwj218a0hmn07.jpg)
