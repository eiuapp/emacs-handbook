

w3m 入门

- https://forum.suse.org.cn/t/emacs-w3m/2918

## 快捷键

- http://kongll.github.io/2015/04/24/Emacs-w3m-%E6%93%8D%E4%BD%9C%E5%BF%AB%E6%8D%B7%E9%94%AE/


## w3m 下如何复制网页中的文字

#### 方法1 下载后复制

下载：

`C-x C-w RET; ~/.w3m/pages/myfirstpage.org`

复制：

这个方式，优点就是，老是要下载文件。

## 问题

### 为什么安装了w3m, 却使用不了？

#### 现象

`M-x package-install RTN w3m RTN` 后，关闭emacs, 然后再打开 emacs, 则 `M-x w3m` 无效，无选项..

#### 解决

- http://jhat.pw/blog/2011/03/05/install-emacs-w3m.html

安装

```bash
sudo apt-get install w3m-el-snapshot
```

### 为什么 lazycat-emacs 下使用不了 w3m?

#### 没有安装w3m

`M-x package-list-packages RTN w3m RTN`

### emacs 科学上网

如何使用到 google 搜索？

默认搜索使用的就是google,但是由于你懂的原因，导致，用google搜索不到内容，那么如何使得 w3m 科学上网呢？

- https://emacs-china.org/t/topic/2808/1
- https://emacs-china.org/t/emacs/9210

#### spacemacs

其实 子龙山人 的配置中，已经有了 

#### w3m 在 emacs 进行 科学上网

##### (可跳过) 

google: `emacs w3m proxy` 找到：

- https://lists.gnu.org/archive/html/help-gnu-emacs/2008-10/msg00046.html
- http://blog.binchen.org/posts/toggle-http-proxy-in-emacs-w3m.html 中的评论处，有提到一个方法

```
(setq w3m-command-arguments
  (nconc w3m-command-arguments
    '("-o" "http_proxy=http://127.0.0.1:6152/")))
```

###### 配置不正确

但是提示： `Error (use-package): w3m/:init: Symbol’s value as variable is void: w3m-command-arguments`

怎么解决？

这说明，配置还是有问题的。

###### 配置正确，要放在 w3m 启动之后

然后，我放在了自己的layer中，配置如下：

```
(defun zilongshanren-tomtsang/init-w3m ()
  (use-package w3m
    :init
    )
  )
(defun zilongshanren-tomtsang/post-init-w3m ()
  ;; w3m post start
  ;; Proxy Gateway
  (setq w3m-command-arguments
        (nconc w3m-command-arguments
               '("-o" "http_proxy=http://127.0.0.1:8118/")))
  ;; w3m post end
)
```

然后在 emacs 中运行 `C-h v w3m-command-arguments RTN`, 确实是有看到 `"-o" "http_proxy=http://127.0.0.1:8118/"`, 成功。

但是，在 emacs 中运行 `M-x w3m RTN`, `g RTN www.google.com` 不成功。

是这个参数，本身不正确，还是参数本身就无效？不明白。有知道的，请告诉我呀...

##### 正确

- https://melpa.org/#/?q=emacs-w3m

找到了 w3m, 然后点击 `github`, 来到

- https://github.com/emacs-w3m/emacs-w3m

再来到

- https://github.com/emacs-w3m/emacs-w3m/blob/8fd65dd9c7d2393ab66c65ee1de67a84dcc779ce/README

其中 `4.3. Proxy Gateway` 中确实是有提到上面的配置。但是，我尝试了，没有成功。

所以，我就尝试 

- 确保 http_proxy 有效：在命令行中运行： `curl --proxy http://127.0.0.1:8118 https://www.reddit.com/`
- 运行`emacs`前，先在命令行中运行： `export http_proxy='http://127.0.0.1:8118'`
- 运行`emacs`：在命令行中运行：`emacs --with-profile spacemacs`

```bash
curl --proxy http://127.0.0.1:8118 https://www.reddit.com/
export http_proxy='http://127.0.0.1:8118'
emacs --with-profile spacemacs
```

然后在 emacs 中运行 `M-x w3m RTN`, `g RTN www.google.com` 成功。

## 配置

陈冰的配置

- https://github.com/wangchen/redguardtoo-emacs.d/blob/master/lisp/init-emacs-w3m.el

## 包

- https://github.com/emacs-w3m/emacs-w3m