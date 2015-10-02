title: hexo部署到gitcafe上静态博客
date: 2015-09-17 00:14:24
tags:
---
## hexo部署到gitcafe上静态博客

hexo这些事儿,[zippera's blog](http://zipperary.com/2013/05/28/hexo-guide-1/),之类的,这些都说的很清楚了.
<h4>
不过也还是有几个特别的地方:

` 想插入图片的时候竟然上不了谷歌.好吧,睡觉,明天继续`

---
 * 在部署deploy的时候,出现<br>`ERROR Deployer not found: git`,<br>加上<br>`npm install hexo-deployer-git --save`,![](http://ww2.sinaimg.cn/large/773d7193gw1ew5uv0hjdmj214y0qigop.jpg)
 之前type是填github,现在是git了,估计是因为有除了github之外的托管博客的网站.
 	* 如果是github, branch也可以不填,默认master.
 	* 是gitcafe的话,就需填上[gitcafe-pages](https://gitcafe.com/GitCafe/Help/wiki/Pages-%E7%9B%B8%E5%85%B3%E5%B8%AE%E5%8A%A9),在repo的时候,可以直接<p>`git remote -v`,
 	![](http://ww1.sinaimg.cn/large/773d7193gw1ew5wa637w6j20n403240i.jpg)
 	
 	<p>参考[链接](https://gitcafe.com/GitCafe/Help/wiki/Pages-%E7%9B%B8%E5%85%B3%E5%B8%AE%E5%8A%A9)建立分支gitcafe-pages.
 	
<h4>
	[gitcafe page帮助](https://gitcafe.com/GitCafe/Help/wiki/Pages-%E7%9B%B8%E5%85%B3%E5%B8%AE%E5%8A%A9),在这里面,因为它现在没有跟github一样的[Github Desktop](https://desktop.github.com/),<br>![](http://ww1.sinaimg.cn/large/773d7193gw1ew5v8x0vlvj209408k74i.jpg)<br>在[配置SSH公钥](https://gitcafe.com/GitCafe/Help/wiki/%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%85%E5%92%8C%E8%AE%BE%E7%BD%AE-Git#wiki)的时候就稍微步骤多了一点点. 

### 我按照官方教程操作,<p>```ssh -T git@gitcafe.com```

一直在最后检测权限的时候出现权限不够,后面我还把~/.ssh文件删除,因为里面包括了github的公钥,我以为是这个原因,后面还是出现Permission denied.
之后我在网上查了一下,加了这个权限就OK了.<p>`chmod 700 ~/.ssh`
<p>


<h7>
### 写markdown这个挺好的--->[mou](http://25.io/mou/),对于像我这样的新手,双屏,可以实时查看,检查错误之类的.

* `hexo clean` <br>挺好用的,你可以试试.

* `hexo s -g ` == `hexo generate` +` hexo server`,在本地查看

	<h6>`INFO  Hexo is running at http://0.0.0.0:4000/. Press Ctrl+C to stop.`

* `hexo d -g ` == `hexo generate` + `hexo deploy`,这就是部署了. 


 	

