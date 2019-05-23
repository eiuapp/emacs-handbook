
chemacs

https://github.com/plexus/chemacs

### 通过chemacs使用spacemacs ###

```bash
cat ~/.emacs-profiles.el

;; (("default" . ((user-emacs-directory . "~/.emacs.d"))))
(("default" . ((user-emacs-directory . "~/.emacs.d")))
 ("spacemacs" . ((user-emacs-directory . "~/spacemacs")
    (env . (("SPACEMACSDIR" . "~/.spacemacs.d")))))
 )

```

有效

运行

```bash
emacs
emacs --with-profiles spacemacs
```

### 通过chemacs使用lazycat-emacs ###

- ubuntu 上已经使用上了 lazycat-emacs
这一部分, 参考 lazycat-emacs 安装

#### 配置 init.el 文件 ####

因为 chemacs 启动的时候, 是通过init.el文件启动的, 而我们的 lazycat 是 site-start.el文件启动的.

```bash
DESKTOP-APB1HCJ% cp ~/lazycat-emacs/site-start.el ~/lazycat-emacs/init.el
DESKTOP-APB1HCJ% vi ~/lazycat-emacs/init.el
DESKTOP-APB1HCJ% cat ~/lazycat-emacs/init.el
(defun add-subdirs-to-load-path (dir)
  "Recursive add directories to `load-path'."
  (let ((default-directory (file-name-as-directory dir)))
    (add-to-list 'load-path dir)
    (normal-top-level-add-subdirs-to-load-path)))
(add-subdirs-to-load-path "/usr/share/emacs/lazycat-u/")

(require 'init)
```

#### 配置 ~/.emacs-profiles.el 文件 ####

```bash
DESKTOP-APB1HCJ% cat ~/.emacs-profiles.el
;; (("default" . ((user-emacs-directory . "~/.emacs.d"))))
(("default" . ((user-emacs-directory . "~/.emacs.d")))
 ("spacemacs" . ((user-emacs-directory . "~/spacemacs")
    (env . (("SPACEMACSDIR" . "~/.spacemacs.d")))))
 ("lazycat" . ((user-emacs-directory . "~/lazycat-emacs"))))
DESKTOP-APB1HCJ%
```

#### 启动 ####

```bash
DESKTOP-APB1HCJ% emacs --with-profile lazycat
```

#### (可选)设置 lazycat-emacs 为默认启动emacs ####

```bash
DESKTOP-APB1HCJ% echo 'lazycat' > ~/.emacs-profile
DESKTOP-APB1HCJ% emacs
```



