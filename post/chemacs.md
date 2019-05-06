
chemacs

https://github.com/plexus/chemacs

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

