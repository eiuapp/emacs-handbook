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

### init-org-roam.el

最后文件主体如下：

```
(require 'org-roam)
(require 'org-roam-server)
(require 'org-roam-protocol)

(setq org-roam-directory "~/install/git/org/roam")

(setq org-roam-server-host "127.0.0.1"
      org-roam-server-port 9090
      org-roam-server-export-inline-images t
      org-roam-server-authenticate nil
      org-roam-server-label-truncate t
      org-roam-server-label-truncate-length 60
      org-roam-server-label-wrap-length 20)
(org-roam-server-mode)

(add-hook 'after-init-hook 'org-roam-mode)

(provide 'init-org-roam)
```

## 127.0.0.1:9090

如果用 chrome 打开 http://127.0.0.1:9090/ 会提示：

```
ch http://127.0.0.1:9090 wants to open this application.
```

- https://superuser.com/questions/1280184/google-chrome-linux-xdg-open-keep-asking-me-forever-what-to-do-with-magnet-l
- https://stackoverflow.com/questions/51986354/how-to-temove-open-xdg-open-dialogue-from-ubuntu-chrome-while-opening-specific-l

有提到下面的方式：
```shell
sudo mkdir -p /etc/opt/chrome/policies/managed/ && echo '{ "URLWhitelist": ["whatsapp://*"] }' |sudo tee /etc/opt/chrome/policies/managed/whitelist.json
```

但是，我好像没有找到这个 ~whatsapp://*~ 这样的东西。怎么办？

