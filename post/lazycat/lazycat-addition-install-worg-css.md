如何在 lazycat-emacs 中为 个性化配置 安装 worg-css 包

## prerequestment

- 完成 lazycat-install-package 的 M4: self/site-lisp/config/init-init.el

## load worg-css/emacs.el

### M1: 直接 load

```
(load "~/lazycat-emacs/self/site-lisp/extensions/worg-css/emacs.el")

;;自动更新blog
(defun my-update-blog-no-commit-message ()
  (interactive)
  (org-publish "worg")
  (shell-command (concat "cd " worg-htmlroot " && git add -A && git ci -m 'update blog' && git push"))
  (shell-command (concat "cd " worg-base " && git add -A && git ci -m 'update blogsrc' && git push")))
;; (global-set-key (kbd "<f6>") 'my-update-blog-no-commit-message)

(defun my-update-blog (commit_message)
  (interactive "sEnter commit message:")
  (org-publish "worg")
  (shell-command (concat "cd " worg-htmlroot " && git add -A && git ci -m '" commit_message "' && git push"))
  (shell-command (concat "cd " worg-base " && git add -A && git ci -m '" commit_message "' && git push")))
;; (global-set-key (kbd "<f6>") 'my-update-blog)

(provide 'init-update-blog)
```

### M2: addition-lazycat-emacs-extension-dir

```
(load "~/lazycat-emacs/self/site-lisp/extensions/worg-css/emacs.el")
```

change to

```
(set addition-lazycat-emacs-extension-dir "~/lazycat-emacs/self/site-lisp/extensions")
(load (concat addition-lazycat-emacs-extension-dir "/worg-css/emacs.el"))
```
### M3: (base M2) addition-lazycat-emacs-extension-dir in init-init.el

many package will use the ~addition-lazycat-emacs-extension-dir~ variable, so set ~addition-lazycat-emacs-extension-dir~ to init-init.el

- self/site-lisp/config/init-init.el

```
  ;; 定义一些启动目录，方便下次迁移修改
  (defvar addition-lazycat-emacs-root-dir (file-truename "~/lazycat-emacs/self/site-lisp"))
  (defvar addition-lazycat-emacs-config-dir (concat addition-lazycat-emacs-root-dir "/config"))
  (defvar addition-lazycat-emacs-extension-dir (concat addition-lazycat-emacs-root-dir "/extensions"))
```

- self/site-lisp/config/init-update-blog.el

remove ~(set addition-lazycat-emacs-extension-dir "~/lazycat-emacs/self/site-lisp/extensions")~

```
 (load (concat addition-lazycat-emacs-extension-dir "/worg-css/emacs.el"))
```

## with-eval-after-load

```
(with-eval-after-load 'org
  (progn
    (load (concat addition-lazycat-emacs-extension-dir "/worg-css/emacs.el"))
    ))
```
## error: Font not available

如果报以下错误：

```
File mode specification error: (error Font not available #<font-spec nil nil 等距更纱黑体 SC nil nil nil nil nil 15.0 nil nil nil ((:name . 等距更纱黑体 SC 15) (:user-spec . 等距更纱黑体 SC 15))>) [220 times]
set-face-attribute: Font not available: #<font-spec nil nil 等距更纱黑体\ SC nil nil nil nil nil 15.0 nil nil nil ((:name . "等距更纱黑体 SC 15") (:user-spec . "等距更纱黑体 SC 15"))>
```

search "等距更纱黑体 SC 15" in lazycat-emacs ，找到 /home/a/lazycat-emacs/site-lisp/config/init-font.el line106, comment this line.

```
;; (set-face-attribute 'width-font-face nil :font "等距更纱黑体 SC 15")
```

restart emacs, then, pass the error.

## error: Symbol’s function definition is void: org-show-all

```
save-current-buffer: Symbol’s function definition is void: org-show-all
```

```
Publishing file /home/a/install/git/wiki/ubuntu/ubuntu-shortcuts.org using ‘org-html-publish-to-html’
[yas] Prepared just-in-time loading of snippets successfully. [3 times]
Eager macro-expansion failure: (error "Don’t know how to make a localized variable an alias") [2 times]
Saving file /home/a/install/git/wiki-html/ubuntu/ubuntu-shortcuts.html...
Wrote /home/a/install/git/wiki-html/ubuntu/ubuntu-shortcuts.html
Publishing file /home/a/install/git/wiki/ubuntu/ubuntu-shortcuts.org using ‘org-org-publish-to-org’
Saving file /home/a/install/git/wiki-html/ubuntu/ubuntu-shortcuts.org...
Wrote /home/a/install/git/wiki-html/ubuntu/ubuntu-shortcuts.org
save-current-buffer: Symbol’s function definition is void: org-show-all
mwheel-scroll: End of buffer [3 times]
Mark set
Making completion list... [2 times]
```

https://emacs.stackexchange.com/questions/51319/symbols-function-defintion-is-void-org-show-all

An error indicating that the symbol's function definition is void usually means that the file containing the function definition has not yet been loaded.
To be of further assistance, it would be helpful to know what version of org-mode you are using -- perhaps you have a stock version that shipped with Emacs and you installed a newer version of org-mode and your installation is confused
If you have the *.el files you can grep them, or there is a grep option for certain versions of grep that can scan gz-ipped files -- search for defun org-show-all to see where it is defined

I guess you have mixed installation in your version string. I think the version you installed fights the built-in version and the built in ~org.el~ does not yet have ~org-show-all~.

- M-x locate-library org  => If you are not sure which org.el is found by Emacs 
- M-x org-version  => print org version
- M-x load-library org => 

~M-x load-library org~ 之后，与贴主一样， ~Symbol’s function definition is void: org-flag-region~

## error: Symbol’s function definition is void: org-flag-region

~M-x locate-library org~ 找到 org-mode 加载的目录是 ~/home/a/install/git/org-mode/lisp~

```
$ pwd
/home/a/install/git/org-mode/lisp
$ grep "org-flag-region" -rl ./      
./org-clock.el
./org-inlinetask.el
./org-macs.el
./org-list.el
./org.el
$ grep "defun org-flag-region" -rn ./
./org-macs.el:688:(defun org-flag-region (from to flag spec)
$ 
```

根据上面的思路，我们找到 ~defun org-flag-region~ 在 ~/install/git/org-mode/lisp/org-macs.el 中，所以加载一下。成功。

如果你没有 org-mode 仓库，可以直接 clone .

```shell
git clone https://code.orgmode.org/bzg/org-mode ~/install/git/org-mode
```

## conclusion

### git clone org-mode

```shell
git clone https://code.orgmode.org/bzg/org-mode ~/install/git/org-mode
```

### git submodule

```shell
git submodule add https://github.com/eiuapp/worg-css.git site-lisp/extensions/worg-css
```

### init-update-blog.el

```
;;; init-update-blog.el --- 更新个人博客wiki

;; (load "~/lazycat-emacs/self/site-lisp/extensions/worg-css/emacs.el")

;; (set addition-lazycat-emacs-extension-dir "~/lazycat-emacs/self/site-lisp/extensions")
;; (load (concat addition-lazycat-emacs-extension-dir "/worg-css/emacs.el"))

(with-eval-after-load 'org
  (progn
    (load (concat addition-lazycat-emacs-extension-dir "/worg-css/emacs.el"))
    ))

(defvar org-mode-dir (file-truename "~/install/git/org-mode/lisp"))
(load (concat org-mode-dir "/org.el"))
(load (concat org-mode-dir "/org-macs.el"))

;; 自动更新blog
(defun my-update-blog-no-commit-message ()
  (interactive)
  (org-publish "worg")
  (shell-command (concat "cd " worg-htmlroot " && git add -A && git ci -m 'update blog' && git push"))
  (shell-command (concat "cd " worg-base " && git add -A && git ci -m 'update blogsrc' && git push")))
;; (global-set-key (kbd "<f6>") 'my-update-blog-no-commit-message)

(defun my-update-blog (commit_message)
  (interactive "sEnter commit message:")
  (org-publish "worg")
  (message "start to push")
  (shell-command (concat "cd " worg-htmlroot " && git add -A && git ci -m '" commit_message "' && git push"))
  (shell-command (concat "cd " worg-base " && git add -A && git ci -m '" commit_message "' && git push")))

(global-set-key (kbd "<f6>") 'my-update-blog)

(provide 'init-update-blog)
```

### init-init.el

~(require 'init-update-blog)~ 加入到 ~init-init.el~ 中