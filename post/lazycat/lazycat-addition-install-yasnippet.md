如何在 lazycat-emacs 中为 个性化配置 安装 yasnippet-snippets

## prerequestment

- 完成 lazycat-install-package 的 M4: self/site-lisp/config/init-init.el
- 查看过关于 lazycat install worg-css 的文章

## thinking
### 原来在 spacemacs 中使用过 yasnippet-snippets
```
 (defun zilongshanren/load-yasnippet ()
   (interactive)
   (unless yas-global-mode
     (progn
       (yas-global-mode 1)
       ;; 提前下载好文件 `git clone https://github.com/AndreaCrotti/yasnippet-snippets ~/emacs/yasnippet-snippets`
       ;; (setq andreacrotti-yasnippet-snippet-dir (expand-file-name "~/emacs/yasnippet-snippets/snippets"))
       (setq my-snippet-dir (expand-file-name "~/.spacemacs.d/site-lisp/extensions/yasnippet-snippets/snippets"))
       ;; https://github.com/joaotavora/yasnippet/blob/master/README.mdown#L88-L92
       ;; 尝试能不能加载多个文件夹,从而可以加载多人的snippets配置
       ;; (setq yas-snippet-dirs '(my-snippet-dir andreacrotti-yasnippet-snippet-dir))
       (setq yas-snippet-dirs '(my-snippet-dir))
       (yas-load-directory my-snippet-dir)
       ;; (yas-load-directory yas-snippet-dirs) ;; 这个写法是错误的,重启后 yas-snippet-dirs 的值会不正确.
       (setq yas-wrap-around-region t)))
       (yas-minor-mode 1))
```

也就是说，我们要加载的snippets文件夹在 ~yasnippet-snippets/snippets~ 中。
### repo
eiuapp's yasnippet repo is:
- https://github.com/eiuapp/yasnippet-snippets
### lazycat-emacs 自身有一个 snippets

- lazycat-emacs/config/init-yasnippet.el

这个配置文件中指出了，加载的就是

~ (add-to-list `yas/root-directory (concat lazycat-emacs-root-dir "/snippets"))~

### 当我们使用自己的 yasnippet 后，那么 lazycat-emacs snippets 会失效

## git submodule

```shell
cd ~/lazycat-emacs/self/ # this is
git submodule add https://github.com/eiuapp/yasnippet-snippets site-lisp/extensions/yasnippet-snippets
```

## init-yasnippet.el

### 复制 lazycat-emacs init-yasnippet.el

```
cp ~/lazycat-emacs/site-lisp/config/init-yasnippet.el ~/lazycat-emacs/self/site-lisp/config/init-yasnippet.el
```

### 修改 yas/root-directory
```
             ;; (add-to-list `yas/root-directory (concat lazycat-emacs-root-dir "/snippets"))
             (add-to-list `yas/root-directory (concat addition-lazycat-emacs-extension-dir "/yasnippet-snippets/snippets"))
```
### init-yasnippet.el

最后文件主体如下：

```
;;; Require
(add-hook 'prog-mode-hook
          '(lambda ()
             (require 'yasnippet)

             (defun get-git-user-name ()
               (interactive)
               (replace-regexp-in-string "\n$" "" (shell-command-to-string "git config --get user.name")))

             (defun get-git-user-email ()
               (interactive)
               (replace-regexp-in-string "\n$" "" (shell-command-to-string "git config --get user.email")))

             ;; (add-to-list `yas/root-directory (concat lazycat-emacs-root-dir "/snippets"))
             (add-to-list `yas/root-directory (concat addition-lazycat-emacs-extension-dir "/yasnippet-snippets/snippets"))
             (yas-global-mode 1)

             ;; Disable yasnippet mode on some mode.
             (dolist (hook (list
                            'term-mode-hook
                            ))
               (add-hook hook '(lambda () (yas-minor-mode -1))))
             ))

(provide 'init-yasnippet)
```
