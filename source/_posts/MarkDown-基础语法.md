---
title: MarkDown 基础语法
date: 2017-04-26 22:03:33
tags: 标签
categories: MarkDown
---
MarkDown是一种轻量级的「标记语言」,它的优点很多,目前也被越来越多的写作爱好者,撰稿者广泛使用。
 ## 下面我们就用简单直观的例子解释MarkDown的基础语法。
<!--more-->

---
# Headings

# 这是 H1 “#”
## 这是 H2 “##”
### 这是 H3 “###”
#### 这是 H4 “####”
##### 这是 H5 “#####”

---
# Emphasis

italics: _underscores_  斜体　

Strong: **two asterisks** 加重

Strikethrough: ~~two tildes~~ 删除线

```
italics: _underscores_  斜体　

Strong: **two asterisks** 加重

Strikethrough: ~~two tildes~~ 删除线
```

---
# Lists

1. List 1
  1. Inner list 1
  2. Inner list 2
2. List 2

```
1. List 1
  1. Inner list 1
  2. Inner list 2
2. List 2
```

---
# Iamge　照片链接
!＋[对照片的表述]＋(照片的网址或者文件夹下地址)

在\hexo\source目录下新建文件夹，命名为images或者其他你喜欢的名字

```
![照片描述](www.baidu.com)

```

---
# Blockquotes 引用格言
As Kanye West said:

> We're living the future so
> the present is our past.

```
As Kanye West said:

> We're living the future so
> the present is our past.
```

---
# Code Blocks 代码

```
$(function() {
  alert("hello world");
});
```

---
# Tables 表格

First Header                | Second Header
----------------------------|-----------------------------
Content from cell 1         | Content from cell 2
Content in the first column | Content in the second column

```
First Header                | Second Header
----------------------------|-----------------------------
Content from cell 1         | Content from cell 2
Content in the first column | Content in the second column
```
