---
layout: post
title: Eclipse Material Design 出现的问题
---

自从 Google Material Design 发布以来，看过了很多 APP 都已应用 Material Design，看到效果，确实狂拽酷炫叼，遂决定自己也了解下，结果出现了两个小问题，在此记录下.
**`项目都是以 Android 5.1.1 进行编译`**
首先，更新最新 ADT，SDK，这里就不多说了，两种方法，[Android SDK 更新方法][1].
接下来，导入 Android V7 support library
这里就遇到了几个问题：
 1. `v7 --> values-large-v14 -> themes_base.xml`  文件中需要进行相关改动，修改为、
  ```
    <resources>
        <style name="Theme.Base.AppCompat.DialogWhenLarge"
           parent="Base.Theme.AppCompat.DialogWhenLarge" />
        <style name="Theme.Base.AppCompat.Light.DialogWhenLarge"
           parent="Base.Theme.AppCompat.Light.DialogWhenLarge" />
    </resources>
  ```

2.部分 dimen name 修改，主要是 `padding & margin` 
原来为 `abc_dialog_padding_top` , 现在最新 `abc_dialog_padding_top_material` 

3. ...


[1]:http://liuz.me/

