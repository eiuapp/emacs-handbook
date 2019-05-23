
(未完成)

lazycat-emacs 安装

## ENV

- env: env-wsl
- os: ubuntu16

## STEP

### 总结

具体配置,可以看一下 https://github.com/eiuapp/lazycat-emacs 的 eiuapp 分支

- 改一下词典的中文名为英文名.
- 修改 sdcv.el 中 format: 1.去 `-x`

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


### lazycat-emacs 安装在已有用户u下 ###

#### 复制环境 ####

为了不影响刚刚新建用户v的 lazycat , 我这里 把 复制到了 `/usr/share/xxy-deepin-emacs-u`

```bash
DESKTOP-APB1HCJ% sudo cp /usr/share/xxy-deepin-emacs/ /usr/share/xxy-deepin-emacs-u/
```

#### 移除 ~/.emacs.d/ ####

```bash
DESKTOP-APB1HCJ% mv ~/.emacs.d/ ~/.emacs.d.wsl-ubuntu16-20190521.bak/
```

#### 把 lazycat-emacs clone 至 ~ 下 ####
#### ln -s site-lisp ####

```bash
DESKTOP-APB1HCJ% sudo rm /usr/share/emacs/lazycat-u
DESKTOP-APB1HCJ% sudo ln -s ~/lazycat-emacs/site-lisp /usr/share/emacs/lazycat-u
DESKTOP-APB1HCJ% ll /usr/share/emacs/lazycat-u/
total 0
drwxr-xr-x 1 u u 4096 May  9 13:49 .
drwxr-xr-x 1 u u 4096 May 10 11:04 ..
drwxr-xr-x 1 u u 4096 May  9 13:49 config
drwxr-xr-x 1 u u 4096 May  9 13:49 extensions
drwxr-xr-x 1 u u 4096 May  9 13:49 pyim-dict
drwxr-xr-x 1 u u 4096 May 10 10:57 sdcv-dict
```

这样, 就可以直接在`~/lazycat-emacs/`就可以有效果了.

#### 配置 site-start.el ####

```bash
DESKTOP-APB1HCJ% cat /usr/share/xxy-deepin-emacs/common/share/emacs/site-lisp/site-start.el
(defun add-subdirs-to-load-path (dir)
  "Recursive add directories to `load-path'."
  (let ((default-directory (file-name-as-directory dir)))
    (add-to-list 'load-path dir)
    (normal-top-level-add-subdirs-to-load-path)))
(add-subdirs-to-load-path "/usr/share/emacs/lazycat/")

(require 'init)

DESKTOP-APB1HCJ% sudo vi /usr/share/xxy-deepin-emacs-u/common/share/emacs/site-lisp/site-start.el
DESKTOP-APB1HCJ% cat /usr/share/xxy-deepin-emacs-u/common/share/emacs/site-lisp/site-start.el
(defun add-subdirs-to-load-path (dir)
  "Recursive add directories to `load-path'."
  (let ((default-directory (file-name-as-directory dir)))
    (add-to-list 'load-path dir)
    (normal-top-level-add-subdirs-to-load-path)))
(add-subdirs-to-load-path "/usr/share/emacs/lazycat-u/")

(require 'init)

DESKTOP-APB1HCJ%
```

#### 启动 ####

```bash
DESKTOP-APB1HCJ% pwd
/usr/share/xxy-deepin-emacs-u/common/bin
DESKTOP-APB1HCJ% ls
ctags  ebrowse  emacs  emacs-26.1  emacsclient  etags
DESKTOP-APB1HCJ% ./emacs
```

完美了, 可以在 u 用户下使用 lazycat-emacs 了.


### 问题(已解决) ###
#### M-x sdcv-search-pointer+ ####

##### 提示 `mpv, mplayer or mpg123 is needed to play word voice` #####

先安装 mpv 吧

http://ubuntuhandbook.org/index.php/2016/07/install-mpv-media-player-ubuntu-16-04/

1. To add PPA, open terminal (Ctrl+Alt+T) and run the command:

```bash
sudo add-apt-repository ppa:mc3man/mpv-tests
```

2. Then upgrade Mpv using Software Updater or just run the command in terminal to install/upgrade it:

```bash
sudo apt update && sudo apt install mpv
```
3. (Optional) To remove the PPA, go to Software & Updates -> Other Software tab. And remove mpv via command:

```bash
sudo apt remove mpv && sudo apt autoremove
```

重启,问题解决.

##### `sdcv-filter sdcv-string is Nothing similar to hero, sorry :` #####

运行 `M-x sdcv-search-pointer+`

```bash
LANG=en_US.UTF-8 sdcv -n -u "懒虫简明英汉词典" -u "懒虫简明汉英词典" -u "KDic11万英汉词典" hero --data-dir=/mnt/c/Users/a/wsl/home/v/lazycat-emacs/site-lisp/sdcv-dict(1:0 top) dir:v git:master text-mode [2019-05-09 19:07]
sdcv-filter sdcv-string is Nothing similar to hero, sorry :
```

因为之前在 spacemacs 下已经成功了,所以我觉得,比较一下不同就可以了.不同点:

- data-dir 
- 用户不同

先假定不受 `用户不同`的影响, 那么,我们就先尝试在命令行能否有返回

因为, wsl下,输入中文会有问题,所以,我先在 词典集 中,复制一个, 让其可在 bash 中运行. 具体操作:
把 `~/lazycat-emacs/site-lisp/sdcv-dict/` 中一个词典复制,修改其中的 `*.ifo` 中的 `bookname` 为英文, 比如, 把 `lazyworm-ec.ifo` 中的 `bookname=lazywormecbak`

如,我们用刚刚这个复制出来的 lazywormecbak 词典, 翻译 `hero` 这个词.
```bash
v@DESKTOP-APB1HCJ:~$ LANG=en_US.UTF-8 sdcv -n -u "lazywormecbak" hero --data-dir=/mnt/c/Users/a/wsl/home/v/lazycat-emacs/site-lisp/sdcv-dict
Found 1 items, similar to hero.
-->lazywormecbak
-->hero

['hiru]
n.
英雄, 男主角, 男主人公

v@DESKTOP-APB1HCJ:~$
```

这样说明,如果我们去修改 仓库中的 `~/lazycat-emacs/site-lisp/config/init-sdcv.el` 的词典 `sdcv-dictionary-simple-list` 为 `lazywormecbak`, 应该要返回一样的结果. 
```bash
(setq sdcv-dictionary-simple-list    ;星际译王屏幕取词词典, 简单, 快速
      '("lazywormecbak"))
;;      '("懒虫简明英汉词典"
;;        "懒虫简明汉英词典"
;;        "KDic11万英汉词典"))
(setq sdcv-dictionary-complete-list     ;星际译王的词典, 完全, 详细
      '(
        "lazywormecbak"
        "懒虫简明英汉词典"
        "英汉汉英专业词典"
        "XDICT英汉辞典"
        "stardict1.3英汉辞典"
        "WordNet"
        "XDICT汉英辞典"
        "Jargon"
        "懒虫简明汉英词典"
        "FOLDOC"
        "新世纪英汉科技大词典"
        "KDic11万英汉词典"
        "朗道汉英字典5.0"
        "CDICT5英汉辞典"
        "新世纪汉英科技大词典"
        "牛津英汉双解美化版"
        "21世纪双语科技词典"
        "quick_eng-zh_CN"
        ))
```
测试. 成功得到返回结果.

从这里看出, 如果我们要在这种情况下, 使用词典, 则要修改一下词典的中文名为英文名.
### 问题(未解决) ###
#### 开启 emacs 时, *message* 提示, `no desktop file` ####











