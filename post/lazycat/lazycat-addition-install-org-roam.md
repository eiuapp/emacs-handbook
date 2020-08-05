如何在 lazycat-emacs 中为 个性化配置 安装 org-roam


## prerequestment

- 完成 lazycat-install-package 的 M4: self/site-lisp/config/init-init.el
- 查看过关于 lazycat install worg-css 的文章

## ref

- https://www.zmonster.me/2020/06/27/org-roam-introduction.html

## error

### "No such file or directory" "emacsql"
```
Error running timer: (file-missing "Cannot open load file" "No such file or directory" "emacsql")
```

因为没有加载 ~emacsql~

git submodule add https://github.com/skeeto/emacsql site-lisp/extensions/emacsql

### error "Cannot find executable \"sqlite3\"!"
```
Error running timer: (error "Cannot find executable \"sqlite3\"!")
```

https://org-roam.discourse.group/t/error-apply-cannot-find-executable-sqlite3/316

```shell
sudo apt-get update
sudo apt-get install sqlite3 libsqlite3-dev
```

### error "Loading file init-org-roam.el failed to provide feature ‘init-org-roam.el’"

```
Error running timer: (error "Loading file /home/a/lazycat-emacs/self/site-lisp/config/init-org-roam.el failed to provide feature ‘init-org-roam.el’")
```

这个是因为在 ~site-lisp/config/init-init.el~ 中require package时错误地多加了 ~.el~ 。如： ~(require 'init-org-roam)~ 写成了 ~(require 'init-org-roam.el)~

## git submodule

```shell
cd ~/lazycat-emacs/self/ # this is
git submodule add https://github.com/org-roam/org-roam site-lisp/extensions/org-roam
git submodule add https://github.com/org-roam/org-roam-server site-lisp/extensions/org-roam-server 
git submodule add https://github.com/skeeto/emacsql site-lisp/extensions/emacsql
git submodule add https://github.com/cireu/emacsql-sqlite3 site-lisp/extensions/emacsql-sqlite3
git submodule add https://github.com/skeeto/emacs-web-server site-lisp/extensions/emacs-web-server
```

## init-org-roam.el

### org-roam-directory

```
(setq org-roam-directory "~/install/git/wiki")
```

这个变量，会使得，当emacs启动后，会自己生成一个 ~org-roam.db~ 的文件（emacsql-sqlite3）

### init-org-roam.el

最后文件主体如下：

```
;;; init-org-roam.el --- org-roam
;; https://www.zmonster.me/2020/06/27/org-roam-introduction.html#org6fd36c4

(require 'org-roam)
(require 'org-roam-server)
(require 'org-roam-protocol)

(setq org-roam-directory "~/install/git/wiki")

(setq org-roam-server-host "127.0.0.1"
      org-roam-server-port 9090
      org-roam-server-export-inline-images t
      org-roam-server-authenticate nil
      org-roam-server-label-truncate t
      org-roam-server-label-truncate-length 60
      org-roam-server-label-wrap-length 20)
(org-roam-server-mode)

(add-hook 'after-init-hook 'org-roam-mode)

(setq org-roam-capture-templates
      '(
        ("d" "default" plain (function org-roam-capture--get-point)
         "%?"
         :file-name "%<%Y%m%d%H%M%S>-${slug}"
         :head "#+title: ${title}\n#+roam_alias:\n\n")
        ("g" "group")
        ("ga" "Group A" plain (function org-roam-capture--get-point)
         "%?"
         :file-name "%<%Y%m%d%H%M%S>-${slug}"
         :head "#+title: ${title}\n#+roam_alias:\n\n")
        ("gb" "Group B" plain (function org-roam-capture--get-point)
         "%?"
         :file-name "%<%Y%m%d%H%M%S>-${slug}"
         :head "#+title: ${title}\n#+roam_alias:\n#+roam_tags: \n\n")))
(add-to-list 'org-roam-capture-templates
             '("t" "Term" plain (function org-roam-capture--get-point)
               "- 领域: %^{术语所属领域}\n- 释义:"
               :file-name "%<%Y%m%d%H%M%S>-${slug}"
               :head "#+title: ${title}\n#+roam_alias:\n#+roam_tags: \n\n"
               :unnarrowed t
               ))
(add-to-list 'org-roam-capture-templates
             '("p" "Paper Note" plain (function org-roam-capture--get-point)
               "* 相关工作\n\n%?\n* 观点\n\n* 模型和方法\n\n* 实验\n\n* 结论\n"
               :file-name "%<%Y%m%d%H%M%S>-${slug}"
               :head "#+title: ${title}\n#+roam_alias:\n#+roam_tags: \n\n"
               :unnarrowed t
               ))

;; ;; org-roam-insert-immediate 不使用 org-roam-capture-templates，
;; ;; 而是使用一个专门的 org-roam-capture-immediate-template 来设置新建内容的模板，
;; ;; 且只能有一个模板，所以设置这个模板的配置是这样的（以默认配置为例）
;; (setq org-roam-capture-immediate-template
;;       '("d" "default" plain (function org-roam-capture--get-point)
;;         "%?"
;;         :file-name "%<%Y%m%d%H%M%S>-${slug}"
;;         :head "#+title: ${title}\n"
;;         :unnarrowed t))

;; ;; org-roam 中可以通过 org-roam-capture-ref-templates 来设置网页捕获相关的模板，默认的设置是这样的
(setq org-roam-capture-ref-templates
      '(("r" "ref" plain (function org-roam-capture--get-point)
         ""
         :file-name "${slug}"
         :head "#+title: ${title}\n#+roam_key: ${ref}\n"
         :unnarrowed t)))

(add-to-list 'org-roam-capture-ref-templates
             '("a" "Annotation" plain (function org-roam-capture--get-point)
               "%U ${body}\n"
               :file-name "${slug}"
               :head "#+title: ${title}\n#+roam_key: ${ref}\n#+roam_alias:\n"
               :immediate-finish t
               :unnarrowed t))

(provide 'init-org-roam)
```

## 127.0.0.1:9090

如果用 chrome 打开 http://127.0.0.1:9090/ 会提示：

```
http://127.0.0.1:9090 wants to open this application.
```

- https://superuser.com/questions/1280184/google-chrome-linux-xdg-open-keep-asking-me-forever-what-to-do-with-magnet-l
- https://stackoverflow.com/questions/51986354/how-to-temove-open-xdg-open-dialogue-from-ubuntu-chrome-while-opening-specific-l

有提到下面的方式：
```shell
sudo mkdir -p /etc/opt/chrome/policies/managed/ && echo '{ "URLWhitelist": ["whatsapp://*"] }' |sudo tee /etc/opt/chrome/policies/managed/whitelist.json
```

但是，我好像没有找到这个 ~whatsapp://*~ 这样的东西。怎么办？

## 小书签org文件加入到org-roam.db

点击了 小书签 后，会到 emacs 中，但是，此时 http://127.0.0.1:9090 中并没有加入刚刚加入的小书签形成的 ~*.org~ 文件，此时 ~M-x org-roam-capture~ 然后选中此 ~*.org~ 文件, 就可以了。
原理可能是 ~M-x org-roam-capture~ 会把此文件，加入到 ~org-roam-directory "~/install/git/org/roam"~ 下的 ~org-roam.db~ 中。