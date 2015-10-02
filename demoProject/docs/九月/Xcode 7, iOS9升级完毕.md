title: Xcode 7, iOS9升级完毕
---
___
## Xcode 7, iOS9升级完毕
<h5>刚刚iMac升级Xcode 7,手机也升了iOS9.
<br>
关于xcode,有人在微博上贴出来了,说通过非官方途径下载的可能会有问题,好多人都去各种网盘,迅雷找资源下载,原因你懂的,天朝的互联网特色嘛.我是在Mac App Store更新的Xcode7, 网络还挺快.

<h6>其中[唐巧_boy](http://weibo.com/u/1708947107?topnav=1&wvr=6&topsug=1#_rnd1442491763317)在他的微博发出来,
![](http://ww1.sinaimg.cn/large/773d7193gw1ew5plu4932j20g70degoz.jpg)
图片是用[微博图床](https://www.google.nl/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCEQFjAAahUKEwjnu6TNhf7HAhXChywKHdKnDks&url=https%3A%2F%2Fchrome.google.com%2Fwebstore%2Fdetail%2F%25E6%2596%25B0%25E6%25B5%25AA%25E5%25BE%25AE%25E5%258D%259A%25E5%259B%25BE%25E5%25BA%258A%2Ffdfdnfpdplfbbnemmmoklbfjbhecpnhf%3Fhl%3Dzh-CN&usg=AFQjCNHVQhI2iAvcdEDoGHzYYdRGjN2-Rw&sig2=yj407F2TkMga8G_3vVFTtQ)上传的,长这样![](http://ww2.sinaimg.cn/large/773d7193gw1ew5pp4eqtaj20li0e5wf6.jpg)
还有一个是[围脖是个好图床](https://chrome.google.com/webstore/detail/%E5%9B%B4%E8%84%96%E6%98%AF%E4%B8%AA%E5%A5%BD%E5%9B%BE%E5%BA%8A/pngmcllbdfgmhdgnnpfaciaolgbjplhe?hl=zh-CN).

<h4>第一个更漂酿,而且有四种选择,第二个围脖是个好图床就只有图片链接,所以微博图床不解释.
---
###打开xcode还是显示load 还是 skip bundle,是因为我装了插件的原因,反正点load就是了. 之后我开始跑代码.现在只发现两个小问题.

* 第一个好像也是自己代码的问题,

<pre>```NSString *lang = [[[UITextInputMode activeInputModes] firstObject] primaryLanguage];```</pre>
这样在之前没啥问题的,现在error了,我就去[stackoverflow](http://stackoverflow.com/questions/3910244/getting-current-device-language-in-ios)搜了一下,有人说私有api,还给我这个链接,我改成这个之后,就OK了.

<pre>```NSString * language = [[NSLocale preferredLanguages] objectAtIndex:0];```</pre>
 #### 后面还一个是bitcode的问题,![](http://ww3.sinaimg.cn/large/773d7193gw1ew5q0cq7n8j20wi01i75n.jpg)

我在Debug里面改了一下,改成No之后就好了.
