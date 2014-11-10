---
layout: post
title: Markdown Learning
---

#### Markdown 记录  
###2014年10月26日 12:41:20  

* 标题显示  
1、在文字下面输入`=`或者`-`(如果有两级以上，使用方法二)

标题- (二级标题)
-

标题= (一级标题)
=

2、用`#`来表示  
# 标题1
## 标题2
### 标题3
#### 标题4
##### 标题5
###### 标题6

* 文本换行方法：  
1、直接在文本后面添加 两个空格  
2、添加`<br/>`强制换行
<br/>
* 添加链接方法：  
1、直接设置链接   
`[链接显示名称][链接]`  
`[Markdown: Basics （快速入门）][http://wowubuntu.com/markdown/basic.html]`<br/>
2、设置链接编号  
[链接显示名称][链接编号]  
`[Markdown 语法说明 (简体中文版)][1]` 
链接编号的定义  
`[1]:http://wowubuntu.com/markdown/basic.html`  
(添加位置随意  个人习惯在底部) 

* 程序代码 首末两行 加上三个 ```+语言(java, C, PHP...)  <br/>
```java
    public class Markdown{
        public static void main(String[] args){
            System.out.println("Hello Markdown...");
        }
    }
```

###2014年10月28日 09:09:35
1、无序列表 使用 `*`、`+`、`-` 进行标识

* 列表1
* 列表2

+ 列表1
+ 列表2

- 列表1
- 列表2

2、有序列表 使用 数字加英文句号 `1.`
1. 有序列表1
2. 有序列表2

3、多层列表显示 `第一层 默认(- + *) 第二层 tab + (- + *) 第三层 ....`

- 外层列表项目
	+ 内层列表项目
		+ 内层无序列表项目
	+ 内层列表项目
- 外层列表项目

4、文本显示处理

- 长文本段内换行 `->`
超长文本怎么进行段内换行
这里应该是第二行文本了

- 文字效果 斜体`单个*号` 粗体`两个*号`
*斜体文字效果*
**粗体文字效果**

- 文字引用效果 `>`
>引用效果

- 分割线 `三个 - `
下面这是一条分割线
---

- 图片链接方式
1、`![图片描述][图片编号] 
![Think][4]  [4]:http://www.liu-zheng.com/img/Think.png
`
![Think][4]
[4]:http://www.liu-zheng.com/img/Think.png
2、`![图片描述](图片链接)
![Think](http://www.liu-zheng.com/img/Think.png)
`
![Think](http://www.liu-zheng.com/img/Think.png)






### 参考链接
[Markdown: Basics （快速入门）][1]<br/>
[Markdown 语法说明 (简体中文版)][2]<br/>
[怎样使用Markdown][3]<br/>

`错误之处  还望大神高手指点！(*^__^*)`

[1]:http://wowubuntu.com/markdown/basic.html
[2]:http://wowubuntu.com/markdown/index.html
[3]:http://www.ituring.com.cn/article/23

























