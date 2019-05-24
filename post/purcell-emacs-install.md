# install #

## clone the repo ##

```bash
mv ~/.emacs.d ~/.emacs.d.bak
git clone https://github.com/purcell/emacs.d.git ~/.emacs.d
```

## checkout your branch ##

```bash
cd ~/.emacs.d
git branch eiuapp
git checkout eiuapp
```

## change melpa address ##

```bash
diff --git a/lisp/init-elpa.el b/lisp/init-elpa.el
index a6ee481..09e86c3 100644
--- a/lisp/init-elpa.el
+++ b/lisp/init-elpa.el
@@ -18,7 +18,7 @@
 (let* ((no-ssl (and (memq system-type '(windows-nt ms-dos))
                     (not (gnutls-available-p))))
        (proto (if no-ssl "http" "https")))
-  (add-to-list 'package-archives (cons "melpa" (concat proto "://melpa.org/packages/")) t)
+  (add-to-list 'package-archives (cons "melpa" (concat proto "://elpa.emacs-china.org/melpa/")) t)
   ;; Official MELPA Mirror, in case necessary.
   ;;(add-to-list 'package-archives (cons "melpa-mirror" (concat proto "://www.mirrorservice.org/sites/melpa.org/packages/")) t)
   (if (< emacs-major-version 24)
```

## configure chemacs ##

```bash
DESKTOP-APB1HCJ% cat ~/.emacs-profiles.el
;; (("default" . ((user-emacs-directory . "~/.emacs.d"))))
(("default" . ((user-emacs-directory . "~/.emacs.d")))
 ("spacemacs" . ((user-emacs-directory . "~/spacemacs")
    (env . (("SPACEMACSDIR" . "~/.spacemacs.d")))))
 ("lazycat" . ((user-emacs-directory . "~/lazycat-emacs")))
 ("purcell" . ((user-emacs-directory . "~/.emacs.d")))

)
DESKTOP-APB1HCJ%
```

## startup ##

```bash
emacs --with-profile purcell
```

wait some minutes, then choose the theme, press "y" twice.

finally, you'll see `;; Happy hacking, u - Emacs ♥ you!`.
