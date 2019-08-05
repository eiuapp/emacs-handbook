
安装 [tommyx-emacs](https://github.com/TommyX12/tommyx-emacs) 

# install #
## clone the repo ##

```bash
git clone --recursive https://github.com/TommyX12/tommyx-emacs.git ~/tommyx-emacs/
```

## checkout your branch ##

```bash
git branch eiuapp
git checkout eiuapp
```

## chemacs ##

创建包下载目录

这个目录,可以自己定义. 因为之前 `~/.emacs.d/`已经使用了,我这里使用 `~/.emacs.d.tommyx-emacs/`

```
mkdir ~/.emacs.d.tommyx-emacs/
```

把 tommyx-emacs 放入 `~/.emacs-profiles.el`

```
DESKTOP-APB1HCJ% cat ~/.emacs-profiles.el
;; (("default" . ((user-emacs-directory . "~/.emacs.d"))))
(("default" . ((user-emacs-directory . "~/.emacs.d")))
 ("tommyx-emacs" . ((user-emacs-directory . "~/.emacs.d.tommyx-emacs/")))
)
DESKTOP-APB1HCJ%
```
这样的话, 等会 tommyx-emacs 启动时,下载的包,就会在这个目录下.

## init.el ##

因为, tommyx-emacs 启动, 需要 启动文件, 如果直接使用 `add-to-emacs.el` 当成 `~/.emacs.d.tommyx-emacs/init.el` 启动的话, 会报错如下:

```
error: Package `use-package-' is unavailable
```
找到下文
https://emacs.stackexchange.com/questions/39250/error-package-use-package-is-unavailable

再结合

https://elpa.emacs-china.org/

做一个 init.el 文件如下:

```
;;; Dependencies
;; require package
(require 'package)

(setq package-archives '(("gnu"   . "http://elpa.emacs-china.org/gnu/")
                         ("org-cn"   . "http://elpa.emacs-china.org/org/")
                         ("melpa" . "http://elpa.emacs-china.org/melpa/"))
      )
;; add melpa stable
(add-to-list 'package-archives
         '("melpa-stable" . "https://stable.melpa.org/packages/"))

;; add melpa
;; (add-to-list 'package-archives
;;              '("melpa" . "http://melpa.milkbox.net/packages/")
;;              )

;; Initialise packages
(package-initialize)

(package-refresh-contents)

;; add use package
(package-install 'use-package)

```

至此, 我们有了`init.el`


## add-to-emacs.el ##

把 `add-to-emacs.el` 的内容放到 `init.el` 文件

```
cat ~/tommyx-emacs/add-to-emacs.el >> ~/.emacs.d.tommyx-emacs/init.el
```

## startup ##

```
emacs --with-profile tommyx-emacs
```

wait some minutes, then 問你是否更新包, press "y" twice.

finally, you'll see `TommyX's Emacs 26.1` 在左上角.

基本上就是安装成功了.
