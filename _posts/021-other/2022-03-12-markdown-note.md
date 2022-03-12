---
layout: post
title: Markdown 语法笔记
description: Markdown 语法笔记
category: 021-other
---


# 前言
> 本文是基于`有道云笔记`md文档编写和测试，如有部分不兼容现象，请在`有道云笔记`进行测试。

# 1. 标题

Markdown 标题有两种格式

__1.1 使用 = 和 - 标记一级和二级标题__
```
一级标题
===
二级标题
---
```

__1.2 使用#号标记__
```
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题
```

# 2. 段落格式

__2.1 段落__

Markdown 段落的几种形
> - 末尾添加两个空格  
> - 使用空行换行
> - 使用四个空格

    使用4个空格的段落
```
使用```的段落(也叫代码块)
echo "hello world";
```

__2.2 字体__

星号与下划线都可以，单是斜体，双是粗体，符号可跨行

- *斜体* `*斜体*`
- _斜体_ `_斜体_`
- **粗体** `**粗体**`
- __粗体__ `__粗体__`
- ***斜体加粗*** `***斜体加粗***`
- ___斜体加粗___ `___斜体加粗___`

```
*这是一个跨行的
斜体语句*
```
*这是一个跨行的
斜体语句*

__2.3 分割线__

三个或更多-_*，必须单独一行，可含空格

```
- - -
___
***
```

__2.4 删除线__
- ~~删除线~~ `~~删除线~~`

__2.5 下划线__
- <u>带下划线文本</u> `<u>带下划线文本</u>`

__2.6 脚注__
```
上标：X<sup>2</sup>，下标：O<sub>2</sub>
```

- 上标：X<sup>2</sup>，下标：O<sub>2</sub>


# 3. 列表

__3.1 无序列表__

语法：无序列表用 - + * 任何一种都可以

```
- git
+ svn
* jenkis

注意：- + * 跟内容之间都要有一个空格
```

__3.2 有序列表__

语法：数字加点

```
1. linux
2. mac
3. win

注意：序号跟内容之间要有空格；
```

__3.3 嵌套列表__

列表嵌套上一级和下一级之前敲三个空格；

示例1：
```
1. go
   - gin
   - iris
   - echo
   - beego
2. python
   - django
3. php
   - laravel
   - lumen
   - hyperf
   - thinkphp
```
1. go
   - gin
   - iris
   - echo
   - beego
2. python
   - django
3. php
   - laravel
   - lumen
   - hyperf
   - thinkphp

示例2：
```
- db
   - es
   - redis
   - mysql
   - clickhouse
- script luanguage
   1. shell
   2. lua
- linux
   - docker
   - k8s
   - nginx
```
- db
   - es
   - redis
   - mysql
   - clickhouse
- script luanguage
   1. shell
   2. lua
- linux
   - docker
   - k8s
   - nginx
   
__3.4 checkbox列表__
```
- [x] huawei
- [x] xiaomi
- [x] apple
   - [ ] iphone
   - [x] ipad
- [ ] vivo
- [ ] oppo
```
- [x] huawei
- [x] xiaomi
- [x] apple
   - [ ] iphone
   - [x] ipad
- [ ] vivo
- [ ] oppo

# 4. 引用

__4.1 引用是在段落开头使用 > 符号 ，然后后面紧跟一个空格符号__

> 引用1  
> 引用2  
> 翻译成html就是`<blockquote></blockquote>`  
> 注意：后面用两个空格来换行  

> 这是一段引用 `> 这是一段引用`
>> 这是一段引用 `>> 这是一段引用`
>>> 这是一段引用 `>>> 这是一段引用`

__4.2 引用与列表的嵌套__
> * 这是`> * `的引用1，空间有个空格  
> * 这是`> * `的引用2，空间有个空格  

> 1. 这是`> 1. `的引用1，空间有个空格  
> 2. 这是`> 2. `的引用2，空间有个空格  


# 5. 图片

语法：

```
![图片alt](图片地址 "图片title")

> 图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
> 图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加
```

示例:

![cmd-markdown-logo](https://www.zybuluo.com/static/img/logo.png)


Markdown 还没有办法指定图片的高度与宽度，如果你需要的话，你可以使用普通的 `<img>` 标签。
```
<img src="https://www.zybuluo.com/static/img/logo.png" width="20%">
```
<img src="https://www.zybuluo.com/static/img/logo.png" width="20%">


# 6. 超链接

__6.1 基本用法__
```
[超链接名](超链接地址 "超链接title")
or
<链接地址>

[mailto:glsn@gmail.com](mailto:glsn@gmail.com)
邮箱地址自动链接 glsn@gmail.com

title可加可不加
```
示例:
> - [开源中国](https://my.oschina.net/wangyaobeijing/blog/4656243)
> - 直接链接：<https://my.oschina.net/wangyaobeijing/blog/4656243>
> - [mailto:glsn@gmail.com](mailto:glsn@gmail.com)
> - 邮箱地址自动链接 glsn@gmail.com


__6.2 引用用法__
```
这个链接用 1 作为网址变量 [google][1]  
这个链接用 2 作为网址变量 [baidu][2]  
然后在文档的结尾为变量赋值

[1]: http://www.google.com/
[2]: http://www.baidu.com/
```

示例:
> - 这个链接用 1 作为网址变量 [google][1]  
> - 这个链接用 2 作为网址变量 [baidu][2]  
> - 然后在文档的结尾为变量赋值

[1]: http://www.google.com/
[2]: http://www.baidu.com/

__6.3 锚点用法__
```
- [10. 流程图](#10-流程图)
- [12. 公式](#11-公式)
```

- [10. 流程图](#10-流程图)
- [12. 公式](#11-公式)

> 注意：-是空格，没有空格就不用-，英文首字母要小写。


# 7. 表格

```
|机型|存储|价格|
|---|:--:|---:|
|ipadpro 2020 | 128GB | 6229|
|ipadpro 2020 | 256GB | 7029|
|ipadpro 2020 | 512GB | 8629|
|ipadpro 2020 | 1TB | 10229|

第二行分割表头和内容

文字默认居左
两边加：表示文字居中
右边加：表示文字居右
注：原生的语法两边都要用 | 包起来，这样兼容性会好一些，不包起来也行

| header 1 | header 3 |
| -------- | -------- |
| cell 1   | cell 2   |
| cell 3   | cell 4   |
| cell 5   | cell 6   |
```

|机型|存储|价格|
|---|:--:|---:|
|ipadpro 2020 | 128GB | 6229|
|ipadpro 2020 | 256GB | 7029|
|ipadpro 2020 | 512GB | 8629|
|ipadpro 2020 | 1TB | 10229|

| header 1 | header 3 |
| -------- | -------- |
| cell 1   | cell 2   |
| cell 3   | cell 4   |
| cell 5   | cell 6   |


# 8. 代码

单行代码：代码之间分别用一个反引号包起来
```
 `代码内容`
```

代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行

````
```go
package main

import (
    "fmt"
)

func main() {
    fmt.Println("Hello Markdown!")
}
```
注意：如果在 ``` 后面跟随语言名称，可以语法高亮
注意：上面的 ``` 是怎么打出来的？外面包4个反引号即可；同理类推，可以包5个
````

# 9. HTML相关

__9.1 支持的 HTML 元素__  

> 不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。  
> 目前支持的 HTML 元素有：`<kbd> <b> <i> <em> <sup> <sub> <br>`等 ，如：  
> 使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑  


__9.2 转义__

```
Markdown中的转义字符为\，转义的有：
\\ 反斜杠
\` 反引号
\* 星号
\_ 下划线
\{\} 大括号
\[\] 中括号
\(\) 小括号
\# 井号
\+ 加号
\- 减号
\. 英文句号
\! 感叹号
```


__9.3 缩写(同HTML的abbr标签)__

即更长的单词或短语的缩写形式，前提是开启识别HTML标签时，已默认开启
```
The <abbr title="Hyper Text Markup Language">HTML</abbr> specification is maintained by the <abbr title="World Wide Web Consortium">W3C</abbr>.
```
The <abbr title="Hyper Text Markup Language">HTML</abbr> specification is maintained by the <abbr title="World Wide Web Consortium">W3C</abbr>.


__9.4 特殊符号 HTML Entities Codes__

```
&copy; & &uml; &trade; &iexcl; &pound;  
&amp; &lt; &gt; &yen; &euro; &reg; &plusmn;  
&para; &sect; &brvbar; &macr; &laquo; &middot;  

X&sup2; Y&sup3; &frac34; &frac14; &times; &divide; &raquo;

18&ordm;C &quot; &apos;
```

&copy; & &uml; &trade; &iexcl; &pound;  
&amp; &lt; &gt; &yen; &euro; &reg; &plusmn;  
&para; &sect; &brvbar; &macr; &laquo; &middot;  

X&sup2; Y&sup3; &frac34; &frac14; &times; &divide; &raquo;

18&ordm;C &quot; &apos;


# 10. 流程图

每个编辑器可能最终呈现会不一样，这里是用的有道云笔记;

#### 流程图
````
```
graph LR
A-->B
```
````

```
graph LR
A-->B
```

#### 序列图
````
```
sequenceDiagram
A->>B: How are you?
B->>A: Great!
```
````

```
sequenceDiagram
A->>B: How are you?
B->>A: Great!
```

#### 甘特图
````
```
gantt
dateFormat YYYY-MM-DD
section S1
T1: 2014-01-01, 9d
section S2
T2: 2014-01-11, 9d
section S3
T3: 2014-01-02, 9d
```
````

```
gantt
dateFormat YYYY-MM-DD
section S1
T1: 2014-01-01, 9d
section S2
T2: 2014-01-11, 9d
section S3
T3: 2014-01-02, 9d
```

-----------------------------------------------------

# 11. 公式

````
```math
E = mc^2
```

```math
\displaystyle
\left( \sum\_{k=1}^n a\_k b\_k \right)^2
\leq
\left( \sum\_{k=1}^n a\_k^2 \right)
\left( \sum\_{k=1}^n b\_k^2 \right)
```

注意：不同的平台可能表现不一样，这里是有道云笔记展示
````

```math
E = mc^2
```

```math
\displaystyle
\left( \sum\_{k=1}^n a\_k b\_k \right)^2
\leq
\left( \sum\_{k=1}^n a\_k^2 \right)
\left( \sum\_{k=1}^n b\_k^2 \right)
```

# 12. Test anchor

---

### 参考链接
- [runoob Markdown 教程](https://www.runoob.com/markdown/md-tutorial.html)
- [Cmd Markdown 编辑阅读器](https://www.zybuluo.com/mdeditor)
- [studygolang Markdown 教程](https://studygolang.com/markdown)
- [Markdown基本语法](https://www.jianshu.com/p/191d1e21f7ed)
- [Markdown简明语法](http://ibruce.info/2013/11/26/markdown/)


> 本文会持续修正及补充，欢迎大家留言纠错。



