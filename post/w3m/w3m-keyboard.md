title: Emacs w3m 操作快捷键 
categories: 
- Technology 
- Keys 
date: 2014-10-30 14:32:15 
tags:
- emacs

https://blog.csdn.net/lnxfei/article/details/43900209

emacs w3m 操作完整版

## 用emacs-w3m理由

1. 平时在emacs里面编辑文档的时候，经常要上网查询一些资料，如果再打开firefox或者谷歌浏览器，不仅费时费力，而且经常会出现一个问题，就是浏览器和emacs两者的窗口经常相互干扰：

当我编辑文档的时候看不见浏览器里面的内容，而当我看浏览器的时候又无法编辑文档。

2. w3m是个文本浏览器，当我看到网页里面合适的内容，可以方便的复制粘贴（我可不提倡抄袭哦^_^），这一点放在firefox或者谷歌的话，就得用鼠标一阵左右键了

3. 这个是最重要的，生活在emacs里面是我的追求，尽管不乏偏执，但是这仍旧是一种追求，所以w3m必然不能缺少

## 基本操作

### 完整的emacs w3m快捷键使用

q: 挂起

Q：退出

C-x k n RET 关闭第n个buffer， 若什么都不输入则关闭当前buffer

U:打开URL

v：打开文件(Bookmarks Aaron.bookmark)，查看书签

G: 在新的标签页中打开URL

g：在当前标签页中打开URL

S：用googl进行搜索(自定义的搜索引擎)

s: 历史(当前标签页的)

H: 主页

R: 刷新

B 返回

N 前进(RET)

RET: 打开衔接

\ 查看源代码

= 查看头信息

u 复制链接地址到剪贴板

c 复制本页地址到剪贴板

M-i 保存当前位置图片

T 显示图片

M-[ 缩小当前图片

M-] 放大当前图片

I 用外部查看器显示当前图片

### 页面操作

C-n 向下一行

C-p 向上一行

C-f 向前

C-b 向后

C-v 向下滚屏

M-v 向上滚屏

> 向右滚屏

< 向左滚屏

, 向左滚一格

. 向右滚一格

C-c C-w 删除当前页

C-c M-w 删除其他页

### 书签操作

a 添加当前页到书签

M-a 添加该URL到书签

C-c C-t 复制当前页到新标签

C-c C-p 上一个标签

C-c C-n 下一个标签

? E 编辑书签

? C-k 删除书

### 焦点操作

M-g 跳到第n行

C-c C-@ 标记当前位置

C-c C-v 跳到上次标记的位置

TAB 下一个衔接

M-TAB 上一个衔接

### 使用百度谷歌搜索

在出现的搜索框回车，然后在buffer会出现TEXT，在它后边输入你想要搜索的东东，然后回车，它就会出现在搜索框，之后再点击搜索的图标即可。其它的类似的搜索都可以这样办，你可通过这种方式登录chinaunix

### 其他重要操作

M 用外部浏览器打开当前页面

M-M 用外部浏览器打开当前URL

C-c C-k 停止载入

C-x C-w RET; ~/.w3m/pages/myfirstpage.org

eg:在emacs w3m下键入a, 然后会有session加入你想要保存到的文件夹的名字即可。如果想访问该文件夹只需要键入v,然后进行相应操作即可

### Good News:

如果在浏览网页时很喜欢这个网页中的内容那么你可以这么做：

C-x C-w RET; ~/.w3m/pages/myfirstpage.org

实现链接编号 

进入 w3m-lnum-mode, M-x w3m-lnum-mode; 按f显示链接编号
