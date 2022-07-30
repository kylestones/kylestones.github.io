---
title: markdown 语法
date: 2016-06-02
---

如何使用Markdown
==
作者：三石
--
上面的两个等同于一级和二级标题即：\# 和\#\#
*** 
--- 
___ 
三个\*, \-, \_均可以用于分割线

## 1. 基本用法

### 1.1 怎样使用斜体

命令： 在需要斜体的文字两边加上\*或者\_即可  
*操作系统：精髓与设计原理*   
_深入理解操作系统_

### 1.2 怎样使用粗体
命令：在需要斜体的文字两边加上两个\*或者\_即可  
__代码大全2__  
**UML用户指南第二版**

### 1.3 怎样使用粗斜体
命令：在需要斜体的文字两边加上三个\*或者\_即可  
***构建之法***  
___编程之美___

### 1.4 文字有背景
`鸟哥的Linux私房菜`

### 1.5 文字中间有删除线效果
~~Effective C++~~  
![编译原理]()

### 1.6 需要阅读的书籍
- [ ] 设计模式
- [ ] C语言程序设计

### 1.7 有序和无序列表

* 算法步骤
+ 算法原理
- 实验结果


1. 检测人脸
3. 人脸对齐
4. 超分重建
5. 人脸识别
2. 后面的即使没有按正确的顺序书写，或者使用无序的都可以（这里无序的好像不支持）


### 1.8
>     前面的符号和文字之间有5个以上的文字，字体效果会有变化
> >     可以嵌套使用，如果想解除嵌套，需要分段

> 没有充分的空格的效果

### 1.9 链接、图片、邮箱
[github](http://www.github.com "title text")上面有大量的优秀的开源代码  
[stackoverflow][1]是一个优秀的程序员论坛

[1]:http://www.stackoverflow.com "点击跳转"

插入图片：![素描](http://imgsrc.baidu.com/forum/w%3D580/sign=9a8f08c1322ac65c6705667bcbf3b21d/0997a1773912b31b105919888118367adab4e171.jpg "素描")

邮箱：<kyleemail@163.com>

### 1.10 代码语法高亮
```c++
#include <iostream>

using namespce std;

int main(){
	int a = 10;
	unsigned int b = -5;
	cout << a + b << endl;
	return 0;
}
```

```bash
#!/usr/bin/env sh
# Compute the mean image from the training leveldb

echo "compute train image mean"

./build/tools/compute_image_mean train_leveldb \
 ./train_mean.binaryproto

echo "Done."
```
```python
#!/usr/bin/env python
#-*- coding:UTF-8-*-

import numpy as np
import cv2
import Tkinter as tk
import Image, ImageTk

import Tkinter
import tkFileDialog
import Image, ImageTk

print "This is a python program!"


```


## 维基百科上面的Markdown语法
Heading
\=======
Sub-heading
\-----------
### Another deeper heading

Paragraphs are separated
by a blank line.

Two spaces at the end of a line leave a  
line break.

Text attributes _italic_, *italic*, __bold__, **bold**, `monospace`.

Horizontal rule:

\---

Bullet list:

  * apples
  * oranges
  * pears

Numbered list:

  1. apples
  2. oranges
  3. pears

[百度](http://www.baidu.com)链接方法  
\[百度\]\(http://www.baidu.com\)





# how to write the code block

    num = 5
    if num > 3:
      print num is lager than three


表格的前后一定要有空行，否则无法生成

First Hello | Second Hea
:----:|:-----:
test | train



`$ a^2 + b^2 = c^2 $`

```math

a^2 + b^2 = c^2

```


```
graph LR
A-->B
```



***
