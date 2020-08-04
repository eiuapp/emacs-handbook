如何在 lazycat-emacs 中为 个性化配置 安装 org-protocol


# prerequestment

- os: ubuntu 18.04
- emacs: 26.3

# Capture web

## ref

- https://stackoverflow.com/questions/7464951/how-to-make-org-protocol-work
- https://cestlaz.github.io/post/using-emacs-70-org-protocol/
- http://tech.memoryimprintstudio.com/org-capture-from-external-applications/
- https://vurt.co.uk/post/org_capture_configuration/
- https://orgmode.org/worg/org-contrib/org-protocol.html
- https://github.com/alphapapa/org-protocol-capture-html

## chrome extension

- https://github.com/sprig/org-capture-extension

## (Optional) argdebug

https://github.com/sprig/org-capture-extension/issues/16#issuecomment-305050310

argdebug

```bash
#!/bin/sh
for x in "$@"; do
        echo >&2 "'$x'"
done
```

确保 ~/usr/bin/argdebug "org-protocol://capture://l/aa/bb/cc"~ 没有问题

```shell
a@a ~/emacs/emacs-26.3/src % /usr/bin/argdebug "org-protocol://capture://l/aa/bb/cc"   
'org-protocol://capture://l/aa/bb/cc'
a@a ~/emacs/emacs-26.3/src % 
```

## xdg-open

确保 ~xdg-open "org-protocol://capture://l/aa/bb/cc"~ 没有问题

如果 emacs server 未开启，显示如下：

```shell
a@a ~/emacs/emacs-26.3/src % xdg-open "org-protocol://capture://l/aa/bb/cc"
/usr/share/xxy-deepin-emacs/common/bin/emacsclient: can't find socket; have you started the server?
/usr/share/xxy-deepin-emacs/common/bin/emacsclient: To start the server in Emacs, type "M-x server-start".
/usr/share/xxy-deepin-emacs/common/bin/emacsclient: No socket or alternate editor.  Please use:

	--socket-name
	--server-file      (or environment variable EMACS_SERVER_FILE)
	--alternate-editor (or environment variable ALTERNATE_EDITOR)
a@a ~/emacs/emacs-26.3/src % 
```

如果 emacs server 已开启，会显示如下：

```shell
a@a ~/emacs/emacs-26.3/src % xdg-open "org-protocol://capture://l/aa/bb/cc"
Waiting for Emacs...%                                                                                                                                                                                                                  
a@a ~/emacs/emacs-26.3/src % 
```

与 xdg-open 相关的问题，可以参考一下：

- https://github.com/sprig/org-capture-extension/issues/16
- https://github.com/sprig/org-capture-extension/pull/30

## add protocol handler

```
$ cat ~/.local/share/applications/org-protocol.desktop                                                                                                                       1 ↵
[Desktop Entry]
Name=org-protocol
Exec=/usr/share/xxy-deepin-emacs/common/bin/emacsclient %u
Type=Application
Terminal=False
Categories=System;
MimeType=x-scheme-handler/org-protocol;
$ cat ~/.local/share/applications/mimeapps.list 
[Added Associations]
x-scheme-handler/org-protocol=org-protocol.desktop
$ 
```

## update-desktop-database

```shell
update-desktop-database ~/.local/share/applications/
sudo update-desktop-database
```
## Configure Emacs

### Init file
```
(server-start)
(require 'org-protocol)
```
### Capture template

You'll probably want to add a capture template something like this:

```
("w" "Web site"
 entry
 (file+olp "/path/to/inbox.org" "Web")
 "* %c :website:\n%U %?%:initial")
```

### init-protocol.el

```
;; (add-to-list 'load-path "~/path/to/org/protocol/")
(add-to-list 'load-path (concat org-mode-root-dir "/lisp/org-protocol.el"))

(require 'server)
;; (server-start)
(unless (server-running-p)
  (server-start));;for emacs client
(require 'org-protocol)

(setq org-protocol-default-template-key "l")
(setq org-capture-templates
 '(
   ("t" "Todo" entry (file+headline "~/install/git/wiki/notes/notes.org" "Tasks")
        "* TODO %?\n  %i\n  %a")
   ;; ("m" "Mail To Do" entry (file+headline "~/Sync/orgfiles/i.org" "To Do and Notes")
   ;;      "* TODO %a\n %?" :prepend t)
   ("l" "Link" entry (file+olp "~/install/git/wiki/notes/notes.org" "Web Links")
        "* %a\n %?\n %i")

   ;; https://ruib.in/posts/one-emacs-to-capture-them-all/
   ("c" "Captured" entry (file ,(concat wiki-root-dir "/notes/capture.org"))
       "* %t %:description\nlink: %l \n\n%i\n" :prepend t :empty-lines-after 1)
   ("n" "Captured Now!" entry (file ,(concat wiki-root-dir "/notes/capture.org"))
       "* %t %:description\nlink: %l \n\n%i\n" :prepend t :emptry-lines-after 1 :immediate-finish t)

   ;; https://stackoverflow.com/questions/7464951/how-to-make-org-protocol-work
   ("w" "Web site" entry (file+olp "/path/to/inbox.org" "Web")
       "* %c :website:\n%U %?%:initial")

   ;; ("l" "Link" entry (file+headline "~/install/git/wiki/notes/notes.org" "Links")
   ;;                  "* %a %^g\n %?\n %T\n %i")
   ("j" "Journal" entry (file+datetree "~/install/git/wiki/notes/journal.org")
        "* %?\nEntered on %U\n  %i\n  %a")
 ))
```

## Configure Chrome

### Make bookmarklet

```
javascript:location.href='org-protocol://capture://w/'+encodeURIComponent(location.href)+'/'+encodeURIComponent(document.title)+'/'+encodeURIComponent(window.getSelection())
```


# Capture script

## M1

- https://stackoverflow.com/questions/7464951/how-to-make-org-protocol-work

```
$ cat /usr/local/bin/org-capture               
#!/bin/bash

if [[ $@ ]]
then
    data="$@"
else
    data=$(cat)
fi

if [[ -z $data ]]
then
    exit 1
fi

encoded=$(python -c "import sys, urllib; print urllib.quote(' '.join(sys.argv[1:]), safe='')" "${data[@]}")

# "link" and "title" are not used, but seem to be necessary to get
# $encoded to be captured
emacsclient "org-protocol://capture://link/title/$encoded"
$ which org-capture 
/usr/local/bin/org-capture
$ tail /var/log/syslog | org-capture
/usr/local/bin/org-capture: line 19: emacsclient: command not found
$ sudo ln -s /usr/share/xxy-deepin-emacs/common/bin/emacsclient /usr/local/bin/emacsclient
$ tail /var/log/syslog | org-capture                                                      
Waiting for Emacs...
$ 
```

因为这里是 ~emacsclient "org-protocol://capture://link/title/$encoded"~ 未匹配到任何一个 ~org-capture-templates~, 那么会根据 ~org-protocol-default-template-key~ 指定的值，进行匹配插入。

比如我们 ~(setq org-protocol-default-template-key "l")~ 指定的是 ~l~，那么会在 

```
("l" "Link" entry (file+olp "~/install/git/wiki/notes/notes.org" "Web Links")
        "* %a\n %?\n %i")
```
~/install/git/wiki/notes/notes.org 文件中的 "Web Links" 小节中插入。


## M2

- https://github.com/alphapapa/org-protocol-capture-html#shell-script


# Adobe Acrobat Reader

- http://tech.memoryimprintstudio.com/org-capture-from-external-applications/

