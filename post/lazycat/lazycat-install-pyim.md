如何在 lazycat-emacs 中为 个性化配置 安装 pyim

## prerequestment

- 完成 lazycat-install-package 的 M4: self/site-lisp/config/init-init.el
- 查看过关于 lazycat install worg-css 的文章

## thinking
### (Optional) File is missing: Cannot open load file, No such file or directory, pyim

if you install pyim by the repo README, you will get the message ~File is missing: Cannot open load file, No such file or directory, pyim~.

- https://emacs-china.org/t/pyim/11901
- (如果安装出错了看这里)https://github.com/tumashu/pyim/issues/316

说明 lazycat 是不会加载单独从 Melpa 中安装包的。:)

### "I don't like Melpa"
如果按照 https://github.com/tumashu/pyim/ 的安装方式，会无法生效。

原因：王勇说了 ~I don't like Melpa~ (https://github.com/manateelazycat/lazycat-emacs/issues/19#issuecomment-504973928)

所以，所有需要 ~M-x package-install~ 的配置，请全部通过 git submodule 加 config/init-* 的方式进行配置吧。

同样的，我们这里也就只能是使用个性化配置的方式使用 pyim 。
## git submodule

```shell
git submodule add https://github.com/tumashu/pyim site-lisp/extensions/pyim
```

## init-pyim

### load pyim

```
(add-to-list 'load-path (concat addition-lazycat-emacs-extension-dir "/pyim/"))
```
或者已经在 ~init-init.el~ 中加入

```
(add-subdirs-to-load-path addition-lazycat-emacs-root-dir)
```

### init-pyim.el

```
(require 'pyim)
(message "require pyim ok")

(setq pyim-punctuation-translate-p '(no yes auto))

(setq default-input-method "pyim") ;; 激活 pyim
(setq pyim-default-scheme 'wubi) ;; 五笔输入
;; (setq pyim-default-scheme 'pyim-shuangpin) ;; 双拼输入模式

;; 让 Emacs 启动时自动加载 pyim 词库
(add-hook 'emacs-startup-hook
            #'(lambda () (pyim-restart-1 t)))

(setq pyim-page-tooltip 'posframe)
(setq pyim-dicts '((:name "基础词库" :file "~/lazycat-emacs/self/site-lisp/utils/pyim/wbdict.pyim")))
;; (setq pyim-dicts '((:name "基础词库" :file '(concat addition-lazycat-emacs-root-dir "/utils/pyim/wbdict.pyim"))))

;; (global-set-key (kbd "C-9") 'toggle-input-method)
(global-set-key (kbd "C-\\") 'toggle-input-method)

(provide 'init-pyim)
```

### init-init.el

~(require 'init-pyim)~ 加入到 ~init-init.el~ 中
