---
layout: post
title: Android Resource Unused Android 无用资源清理错误
---

最近发现一个很好用的无用资源清理插件 **AndroidResourceCleaner**

github 地址：
[AndroidResourceCleaner](https://github.com/NashLegend/AndroidResourceCleaner)

简单使用介绍：
[一个自动清理Android项目无用资源的工具类及源码](http://nashlegend.blog.51cto.com/5635342/1657683)


但是在个人使用过程中，根据上面使用介绍，将 AndroidUnusedResources.jar 放置项目根目录，运行命令 `java -jar AndroidUnusedResources.jar >del.txt` 出现如下问题

`Unable to determine your application's package name from AndroidManifest.xml.  Please ensure it is set.`

通过各方面检查，都没有问题，无奈之下，寻求谷哥帮助，最后绕来绕去还是在 github 上找到解决方法   ps. 貌似是个韩国的程序猿
 
[问题解决办法地址](http://lsit81.tistory.com/entry/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%A6%AC%EC%86%8C%EC%8A%A4-%EC%9E%90%EB%8F%99-%EC%A0%9C%EA%B1%B0)

在文章中有这么一句话
`주의  : 작업된 프로젝트의 인코딩 속성에 맞게 -Dfile.encoding 옵션을 바꿔 주셔야 한글이 깨지지 않습니다`

原谅不懂韩文，通过 Google 翻译明白了大致意思是说，根据项目编码需要添加 `-Dfile.encoding` 参数


后来通过查看项目实际编码，发现项目使用的是 U8 的编码，所以会提示上述错误，添加 `-Dfile.encoding` 参数，问题解决

最终执行命令为 `java -Dfile.encoding=UTF-8 -jar AndroidUnusedResources.jar >del.txt` 





