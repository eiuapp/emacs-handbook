
(未完成)

lazycat-emacs 安装

## ENV

- os: ubuntu16

## STEP


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

https://github.com/emacs-mirror/emacs/blob/master/INSTALL

看了一下, 然后找到

https://github.com/favadi/build-emacs

执行一下这里的脚本.

```bash
./build-emacs.sh
```

没问题,安装成功.

### 安装 deepin-emacs ###

尝试用 build-emacs.sh 中的方法去安装 deepin-emacs

```bash
sudo mkdir -p /usr/share/xxy-deepin-emacs/common
./configure --prefix=/usr/share/xxy-deepin-emacs/common --with-xft --with-x-toolkit=gtk3 
make 
sudo make install
```

Install Deepin emacs

```bash
sudo cp ./site-start.el /usr/share/xxy-deepin-emacs/common/share/emacs/site-lisp/
sudo cp -r ./site-lisp /usr/share/xxy-deepin-emacs
sudo ln -s /usr/share/xxy-deepin-emacs/common/bin/emacs /usr/bin/xxy-deepin-emacs
```

启动

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



### lazycat-emacs ###










