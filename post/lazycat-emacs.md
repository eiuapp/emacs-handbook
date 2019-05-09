
(未完成)

lazycat-emacs 安装

## ENV

- os: ubuntu16

## STEP

### (可跳过)前期工作 ###

```bash
DESKTOP-APB1HCJ% pwd
/mnt/c/Users/a/emacs/lazycat
DESKTOP-APB1HCJ% ls
emacs  lazycat-emacs  lazycat-emacs.origin  lazycat-emacs.origin.20190505
DESKTOP-APB1HCJ% ls /usr/share/emacs
26.2  site-lisp
DESKTOP-APB1HCJ% sudo ln -s /mnt/c/Users/a/emacs/lazycat/lazycat-emacs/site-lisp /usr/share/emacs/lazycat
DESKTOP-APB1HCJ% ls /usr/share/emacs
26.2  lazycat  site-lisp
DESKTOP-APB1HCJ% ls /usr/share/emacs/site-lisp
autoconf  debian-startup.el  desktop-entry-mode.el  dictionaries-common  subdirs.el
DESKTOP-APB1HCJ% sudo cp /mnt/c/Users/a/emacs/lazycat/lazycat-emacs/site-start.el /usr/share/emacs/site-lisp/
DESKTOP-APB1HCJ% ls /usr/share/emacs
26.2  lazycat  site-lisp
DESKTOP-APB1HCJ% ls /usr/share/emacs/site-lisp
autoconf  debian-startup.el  desktop-entry-mode.el  dictionaries-common  site-start.el  subdirs.el
DESKTOP-APB1HCJ% emacs
```

这个时候, 报错如下:

```bash
Eager macro-expansion failure: (void-function -map)
set-face-attribute: Font not available: #<font-spec nil nil Droid\ Sans\ Mono-14 nil nil nil nil nil nil nil nil nil ((:name . "Droid Sans Mono-14") (:user-spec . "Droid Sans Mono-14"))>
user-error: Minibuffer window is not active
```

看一下 Font not available 的问题

https://github.com/syl20bnr/spacemacs

https://github.com/adobe-fonts/source-code-pro

https://github.com/adobe-fonts/source-code-pro/issues/17#issuecomment-8967116

这里应该是没有安装,所以,安装一下

最后是 https://askubuntu.com/questions/193072/how-to-use-the-adobe-source-code-pro-font 


安装完成.

然后,发现 安装的操作系统不一致,还是会有一些麻烦,所以,找一下历史版本是否有debian系统,很幸运地找到了.

从 fork 里找到了 deepin-emacs, 下面这个相对 commit 数最大,为 445

https://github.com/xuxiaoyu2010/deepin-emacs

按照这个上面的 README.org 文件. 走到 ./configure 这一步,报错如下

```bash
checking for gif_lib.h... yes
checking for GifMakeMapObject in -lgif... yes
configure: error: The following required libraries were not found:
     gnutls
Maybe some development libraries/packages are missing?
To build anyway, give:
     --with-gnutls=ifavailable
as options to configure.
DESKTOP-APB1HCJ%
```


尝试去除 `--with-x-toolkit=gtk3` 因为我们这里的 xserver 是通过 MobaXterm_Personal_11.1.exe . 

`./configure --prefix=/usr/share/deepin-emacs/common `

还是会报一样的错误


https://stackoverflow.com/questions/52722096/build-emacs-and-gnutls-not-found

方法1 

```bash
apt-cache search libgnutls
```

然后安装相应的包.

方法2 

```bash
./configure --prefix=/usr/share/deepin-emacs/common --with-x-toolkit=gtk3 --with-gnutls=ifavailable
```

我用 ./configure --prefix=/usr/share/deepin-emacs/common --with-x-toolkit=gtk3 --with-gnutls=ifavailable 

然后 make ,又报下面的错误

```bash
Loading /mnt/c/Users/a/emacs/lazycat/emacs/lisp/emacs-lisp/lisp.el (source)...
Wrong type argument: char-table-p, nil
Makefile:807: recipe for target 'bootstrap-emacs.pdmp' failed
make[1]: *** [bootstrap-emacs.pdmp] Error 255
make[1]: Leaving directory '/mnt/c/Users/a/emacs/lazycat/emacs/src'
Makefile:424: recipe for target 'src' failed
make: *** [src] Error 2
DESKTOP-APB1HCJ%
```

回到又用 configure 的方法1

```bash
sudo apt-get install libgnutls-dev
./configure --prefix=/usr/share/deepin-emacs/common --with-x-toolkit=gtk3 
make
```

还是报一样的错误

回想一下, 我们这一步的目的就是 编译安装 emacs , 所以, 

http://ergoemacs.org/emacs/building_emacs_from_git_repository.html

http://ergoemacs.org/emacs/building_emacs_on_linux.html

运行 

```bash
sudo apt-get install build-essential
sudo apt-get build-dep emacs24
```

还是会报错.

### shell 编译安装 emacs ###


https://github.com/emacs-mirror/emacs/blob/master/INSTALL

看了一下, 然后找到

https://github.com/favadi/build-emacs

执行一下这里的脚本.

```bash
./build-emacs.sh
```

没问题,安装成功.

### 编译安装 emacs ###

尝试用 build-emacs.sh 中的方法去安装 deepin-emacs

```bash
sudo mkdir -p /usr/share/xxy-deepin-emacs/common
./configure --prefix=/usr/share/xxy-deepin-emacs/common --with-xft --with-x-toolkit=gtk3 
make 
sudo make install
```

安装完毕,则意味着2点:

- 启动文件在 `/usr/share/xxy-deepin-emacs/common/bin/` 中
- 启动配置中的 site-start.el 应该放在 `/usr/share/xxy-deepin-emacs/common/share/emacs/site-lisp/` 中

### (可跳过)安装 deepin-emacs ###

#### Install Deepin emacs

```bash
sudo cp ./site-start.el /usr/share/xxy-deepin-emacs/common/share/emacs/site-lisp/
sudo cp -r ./site-lisp /usr/share/xxy-deepin-emacs
sudo ln -s /usr/share/xxy-deepin-emacs/common/bin/emacs /usr/bin/xxy-deepin-emacs
```

#### 启动

```bash
which xxy-deepin-emacs
xxy-deepin-emacs
```

报错如下

```bash
Eager macro-expansion failure: (void-function -map)
set-face-attribute: Font not available: #<font-spec nil nil Droid\ Sans\ Mono-14 nil nil nil nil nil nil nil nil nil ((:name . "Droid Sans Mono-14") (:user-spec . "Droid Sans Mono-14"))>
```

这到底是个什么错误?

报错信息中提到了 `Droid Sans Mono`

搜索 `ubuntu 安装 Droid Sans Mono`

https://www.jianshu.com/p/ed098f15f638

```bash
sudo apt-get install ttf-droid
```

报错误

```
E: Package 'ttf-droid' has no installation candidate
```

https://blog.csdn.net/weixin_33895695/article/details/85552268

```bash
sudo apt-get install fonts-droid-fallback
```

再启动

```bash
which xxy-deepin-emacs
xxy-deepin-emacs
```

报错依旧

提issue, https://github.com/manateelazycat/lazycat-emacs/issues/17

经过回答,是另一个思路,换成其它字体.

### 换字体

找到字体的位置

因为, 在 deepin-emacs 中没有找到这个 字体,我又回到最新的 lazycat-emacs




### lazycat-emacs ###

为不再污染 用户之前的 emacs 设置, 决定,新建立一个用户v, 并设置好 ${HOME} 地圵

#### 编译 emacs 

之前,做过了,不做了, 总之是,编译到 `/usr/share/xxy-deepin-emacs/common/` 中了.

#### 配置 lazycat-emacs

clone the repository

```bash
git clone https://github.com/manateelazycat/lazycat-emacs/ ~
```

Build my config symlink to emacs directory:

```bash
sudo ln -s ~/lazycat-emacs/site-lisp /usr/share/emacs/lazycat
```
做软链接,方便本地修改.
或者
```bash
sudo cp -r ~/lazycat-emacs/site-lisp/ /usr/share/emacs/lazycat
```

Copy site-start.el in emacs directory to start my config:

```bash
sudo cp ~/lazycat-emacs/site-start.el /usr/share/xxy-deepin-emacs/common/share/emacs/site-lisp/
```

这个 site-start.el 文件,是会加载刚刚我们放进去的目录,所以如果刚刚放入 /usr/share/emacs 中的不是这个目录, 则要修改一下目录地圵.

```
(add-subdirs-to-load-path "/usr/share/emacs/lazycat")
```

比如

```bash
DESKTOP-APB1HCJ% cat /usr/share/xxy-deepin-emacs/common/share/emacs/site-lisp/site-start.el
(defun add-subdirs-to-load-path (dir)
  "Recursive add directories to `load-path'."
  (let ((default-directory (file-name-as-directory dir)))
    (add-to-list 'load-path dir)
    (normal-top-level-add-subdirs-to-load-path)))
(add-subdirs-to-load-path "/usr/share/emacs/lazycat/site-lisp/")

(require 'init)
DESKTOP-APB1HCJ%
```

#### 修改字体

因为我们这里的字体问题, 修改成之前为了spacemacs而安装的字体 `Source Code Pro` 

```bash
DESKTOP-APB1HCJ% sudo head lazycat/site-lisp/extensions/lazycat-theme/lazycat-theme.el | grep emacs-font-name
(defvar emacs-font-name ""
  (setq emacs-font-name "Monaco"))
  (setq emacs-font-name "Source Code Pro")))
DESKTOP-APB1HCJ%
```

#### Start emacs:

```
cd /usr/share/xxy-deepin-emacs/common/bin/
./emacs
```

### 问题 ###

#### M-x sdcv-search-pointer+ ####

提示 `mpv, mplayer or mpg123 is needed to play word voice`


#### 开启 emacs 时, *message* 提示, `no desktop file` ####











