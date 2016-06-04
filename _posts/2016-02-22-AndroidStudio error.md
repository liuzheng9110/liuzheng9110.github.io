---
layout: post
title: AndroidStudio 问题集锦
---




01. Gradle DSL method not found: 'android() http://blog.csdn.net/u012964796/article/details/47000991
02. 使用或覆盖了已过时的 API。有关详细信息请使用-Xlint:deprecation重新编译 http://www.crifan.com/android_studio_build_osmand_warning_use_deprecated_api_for_detail_use_xlint_deprecation_rebuild/
03. the file is indented with tabs instead of 4 spaces  http://stackoverflow.com/questions/23632624/android-studio-tab-spacing You will find Editor -> Code Style->Java->Tabs and Indents->Use tab character.
04. AS 覆盖更新之后，启动出现 project refesh failed   注意覆盖之后之前版本 jar 是否已经覆盖或删除  android-studio/plugins/gradle/lib  http://stackoverflow.com/questions/34216758/android-studio-gradle-error-buildactionexecuter-withcancellationtoken/34464054
05. AS 更新 gradle 出现 'dependencies' cannot be applied to '(groovy.lang.Closure)'    http://stackoverflow.com/questions/29769988/dependencies-cannot-be-applied-to-groovy-lang-closure




 自定义注释模版	http://blog.csdn.net/sun_promise/article/details/45642319
 显示行号		http://jingyan.baidu.com/article/e5c39bf5a522e539d76033d8.html
 本地配置 Gradle 加快启动速度  http://my.oschina.net/xesam/blog/213953?fromerr=f6Hx2JAt


 build.gradle 相关设置  dependencies
  引入 maven 仓库	 compile 'package_name:maven_name:version'  // compile 'com.google.code.gson:gson:2.4'
  引入本地 module	 compile project (':module_name')
  引入本地 libs/jar	 compile files('libs/volley.jar')
  

