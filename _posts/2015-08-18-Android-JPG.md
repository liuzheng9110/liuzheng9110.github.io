---
layout: _post
title: Android中decode JPG时建议使用inPreferQualityOverSpeed
---

在BitmapFactory.decodeBitmap方法中，参数BitmapFactory.Options里有一项是inPreferQualityOverSpeed：设为true的话，画质更好，加载时间略长一些。默认为false。

经过试验，发现对画质影响挺明显的。建议各个开发者对画质敏感的app都设为true。

下面是我的试验结果，你可以下载我这个测试app自己改参数做试验：
http://files.cnblogs.com/files/zhucai/TestJPG.apk

这个是以100的品质循环加载保存10次后的结果，前面是原图，后面是结果图：
这张是inPreferQualityOverSpeed为false的:



这张是inPreferQualityOverSpeed为true的:





via: http://weibo.com/p/1001603876907409367928
