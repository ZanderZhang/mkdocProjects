title: 工程移除CocoaPods依赖库
date: 2015-09-26 10:52:17
tags:
---
## 工程移除CocoaPods依赖库
点这里--->[CocoaPods安装和使用教程](http://code4app.com/article/cocoapods-install-usage)

<br>当我们工程安装很多第三方开源类库,有时候不需要时,我们可以将其移除.<br>
在stackoverflow发现[How to remove CocoaPods from a project?](http://stackoverflow.com/questions/16427421/how-to-remove-cocoapods-from-a-project)

<br>第二个answer比较简单

需要用到两个`CocoaPods plugin`

*   [cocoapods-deintegrate](https://github.com/kylef/cocoapods-deintegrate)
	* 安装`gem install cocoapods-deintegrate`
	* 运行`pod deintegrate`

这一步之后就剩下<pre>Podfile
Podfile.lock
Workspace</pre>

* 可以手动移除剩下的这三个,也可以用到[cocoapods-clean](https://github.com/BendingSpoons/cocoapods-clean)
	* 安装`gem install cocoapods-clean`
	* 运行`pod clean`
	* 最后运行`rm Podfile`移除`Podfile`
	
如果还存在问题,可以把之前用到的库的路径移除,![](http://ww1.sinaimg.cn/large/773d7193gw1ewfofs3rz0j20ne03u0tx.jpg)

###项目目录下,在你的终端就是这样的顺序:
<pre>gem install cocoapods-deintegrate
pod deintegrate
gem install cocoapods-clean
pod clean
rm Podfile
</pre>

最后你可以在`Podfile`添加新的库使用,或不使用`CocoaPods`,当然还有[Carthage](https://github.com/Carthage/Carthage).

## <font color=red>记得备份你的项目!

