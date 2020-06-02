在 mac 下安装 lazycat-emacs

## 结论

- lazycat-emacs 文件夹可放在任意位置
- 包下载目录（这里是`~/.emacs.d.lazycat-emacs/`) 可放在任意位置
- 要配置 cache-path-from-shell

## 第一次启动

```
File is missing: Cannot open load file, No such file or directory, /Users/tomtsang/lazycat-emacs/init.el
```

所以，我们没有 init.el

## 创建一个 init.el 文件

把 cat site-start.el 放入这个 init.el 中

## (错误，可跳过)把 init.el 放在 ~/lazycat-emacs/

返回到 ~/lazycat-emacs/ 中启动

```
This is likely to cause problems...
Consider using a subdirectory instead, e.g.: /Users/tomtsang/lazycat-emacs/lisp
```

那就创建文件夹

```
mkdir -p  ~/lazycat-emacs/lisp
```

运行后，会出现 迭代引用文件，所以，这肯定不行的。

## (错误，可跳过)把 init.el 放在 ~/.emacs.d.lazycat-emacs/

```
mkdir -p  ~/.emacs.d.lazycat-emacs/
cat site-start.el >> ~/.emacs.d.lazycat-emacs/init.el
```

运行

```
File is missing: Cannot open load file, No such file or directory, benchmark-init-modes
```

根据提示

```
emacs --with-profile lazycat --debug-init
```

得到下面的报错信息

```
Debugger entered--Lisp error: (file-missing "Cannot open load file" "No such file or directory" "benchmark-init-modes")
  require(benchmark-init-modes)
  (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (require 'benchmark-init-modes) (require 'benchmark-init) (benchmark-init/activate) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore)))))
  (unwind-protect (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (require 'benchmark-init-modes) (require 'benchmark-init) (benchmark-init/activate) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore))))) (and with-temp-message (if current-message (message "%s" current-message) (message nil))))
  (let ((with-temp-message "") (current-message)) (unwind-protect (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (require 'benchmark-init-modes) (require 'benchmark-init) (benchmark-init/activate) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore))))) (and with-temp-message (if current-message (message "%s" current-message) (message nil)))))
  (let ((gc-cons-threshold most-positive-fixnum) (file-name-handler-alist nil)) (defvar lazycat-emacs-root-dir (file-truename "~/lazycat-emacs/site-lisp")) (defvar lazycat-emacs-config-dir (concat lazycat-emacs-root-dir "/config")) (defvar lazycat-emacs-extension-dir (concat lazycat-emacs-root-dir "/extensions")) (defvar lazycat-emacs-sdcv-data-dir (concat lazycat-emacs-root-dir "/sdcv-dict")) (let ((with-temp-message "") (current-message)) (unwind-protect (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (require 'benchmark-init-modes) (require 'benchmark-init) (benchmark-init/activate) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore))))) (and with-temp-message (if current-message (message "%s" current-message) (message nil))))))
  eval-buffer(#<buffer  *load*-448603> nil "/Users/tomtsang/lazycat-emacs/site-lisp/config/init.el" nil t)  ; Reading at buffer position 2314
  load-with-code-conversion("/Users/tomtsang/lazycat-emacs/site-lisp/config/init.el" "/Users/tomtsang/lazycat-emacs/site-lisp/config/init.el" nil t)
  require(init)
  eval-buffer(#<buffer  *load*-520146> nil "/Users/tomtsang/.emacs.d.lazycat-emacs/init.el" nil t)  ; Reading at buffer position 1036
  load-with-code-conversion("/Users/tomtsang/.emacs.d.lazycat-emacs/init.el" "/Users/tomtsang/.emacs.d.lazycat-emacs/init.el" nil nil)
  load("/Users/tomtsang/.emacs.d.lazycat-emacs/init.el")
  (let* ((emacs-directory (file-name-as-directory (chemacs-emacs-profile-key 'user-emacs-directory))) (init-file (expand-file-name "init.el" emacs-directory)) (custom-file- (chemacs-emacs-profile-key 'custom-file init-file)) (server-name- (chemacs-emacs-profile-key 'server-name))) (setq user-emacs-directory emacs-directory) (if server-name- (progn (setq server-name server-name-))) (mapcar (function (lambda (env) (setenv (car env) (cdr env)))) (chemacs-emacs-profile-key 'env)) (load init-file) (if (not custom-file) (progn (setq custom-file custom-file-) (load custom-file))))
  chemacs-load-profile("lazycat")
  (cond ((equal (car args) "--with-profile") (add-to-list 'command-switch-alist '("--with-profile" lambda (_) (pop command-line-args-left))) (chemacs-load-profile (car (cdr args)))) ((equal (car s) "--with-profile") (add-to-list 'command-switch-alist (cons (car args) '(lambda (_)))) (chemacs-load-profile (mapconcat 'identity (cdr s) "="))) (t (chemacs-check-command-line-args (cdr args))))
  (let ((s (split-string (car args) "="))) (cond ((equal (car args) "--with-profile") (add-to-list 'command-switch-alist '("--with-profile" lambda (_) (pop command-line-args-left))) (chemacs-load-profile (car (cdr args)))) ((equal (car s) "--with-profile") (add-to-list 'command-switch-alist (cons (car args) '(lambda (_)))) (chemacs-load-profile (mapconcat 'identity (cdr s) "="))) (t (chemacs-check-command-line-args (cdr args)))))
  (if args (let ((s (split-string (car args) "="))) (cond ((equal (car args) "--with-profile") (add-to-list 'command-switch-alist '("--with-profile" lambda (_) (pop command-line-args-left))) (chemacs-load-profile (car (cdr args)))) ((equal (car s) "--with-profile") (add-to-list 'command-switch-alist (cons (car args) '(lambda (_)))) (chemacs-load-profile (mapconcat 'identity (cdr s) "="))) (t (chemacs-check-command-line-args (cdr args))))) (chemacs-load-profile (chemacs-detect-default-profile)))
  chemacs-check-command-line-args(("--with-profile" "lazycat"))
  (cond ((equal (car args) "--with-profile") (add-to-list 'command-switch-alist '("--with-profile" lambda (_) (pop command-line-args-left))) (chemacs-load-profile (car (cdr args)))) ((equal (car s) "--with-profile") (add-to-list 'command-switch-alist (cons (car args) '(lambda (_)))) (chemacs-load-profile (mapconcat 'identity (cdr s) "="))) (t (chemacs-check-command-line-args (cdr args))))
  (let ((s (split-string (car args) "="))) (cond ((equal (car args) "--with-profile") (add-to-list 'command-switch-alist '("--with-profile" lambda (_) (pop command-line-args-left))) (chemacs-load-profile (car (cdr args)))) ((equal (car s) "--with-profile") (add-to-list 'command-switch-alist (cons (car args) '(lambda (_)))) (chemacs-load-profile (mapconcat 'identity (cdr s) "="))) (t (chemacs-check-command-line-args (cdr args)))))
  (if args (let ((s (split-string (car args) "="))) (cond ((equal (car args) "--with-profile") (add-to-list 'command-switch-alist '("--with-profile" lambda (_) (pop command-line-args-left))) (chemacs-load-profile (car (cdr args)))) ((equal (car s) "--with-profile") (add-to-list 'command-switch-alist (cons (car args) '(lambda (_)))) (chemacs-load-profile (mapconcat 'identity (cdr s) "="))) (t (chemacs-check-command-line-args (cdr args))))) (chemacs-load-profile (chemacs-detect-default-profile)))
  chemacs-check-command-line-args(("/Applications/Emacs.app/Contents/MacOS/Emacs-x86_64-10_10" "--with-profile" "lazycat"))
  eval-buffer(#<buffer  *load*> nil "/Users/tomtsang/.emacs" nil t)  ; Reading at buffer position 6290
  load-with-code-conversion("/Users/tomtsang/.emacs" "/Users/tomtsang/.emacs" t t)
  load("~/.emacs" t t)
  #f(compiled-function () #<bytecode 0x400d3941>)()
  command-line()
  normal-top-level()
```

从中可以看到：

- 确实是在 `~/.emacs.d.lazycat-emacs/` 中进行了安装包
- 报错是因为 ~/lazycat-emacs/site-lisp/config/init.el 中的 require 语句

那么我们跑进去，注释掉，即可。

然后，又出现了

```
Debugger entered--Lisp error: (file-missing "Cannot open load file" "No such file or directory" "exec-path-from-shell")
  require(exec-path-from-shell)
  eval-buffer(#<buffer  *load*-511362> nil "/Users/tomtsang/lazycat-emacs/site-lisp/extensions/cache-path-from-shell/cache-path-from-shell.el" nil t)  ; Reading at buffer position 2728
  load-with-code-conversion("/Users/tomtsang/lazycat-emacs/site-lisp/extensions/cache-path-from-shell/cache-path-from-shell.el" "/Users/tomtsang/lazycat-emacs/site-lisp/extensions/cache-path-from-shell/cache-path-from-shell.el" nil t)
  require(cache-path-from-shell)
  (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore)))))
  (unwind-protect (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore))))) (and with-temp-message (if current-message (message "%s" current-message) (message nil))))
  (let ((with-temp-message "") (current-message)) (unwind-protect (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore))))) (and with-temp-message (if current-message (message "%s" current-message) (message nil)))))
  (let ((gc-cons-threshold most-positive-fixnum) (file-name-handler-alist nil)) (defvar lazycat-emacs-root-dir (file-truename "~/lazycat-emacs/site-lisp")) (defvar lazycat-emacs-config-dir (concat lazycat-emacs-root-dir "/config")) (defvar lazycat-emacs-extension-dir (concat lazycat-emacs-root-dir "/extensions")) (defvar lazycat-emacs-sdcv-data-dir (concat lazycat-emacs-root-dir "/sdcv-dict")) (let ((with-temp-message "") (current-message)) (unwind-protect (progn (if with-temp-message (progn (setq current-message (current-message)) (message "%s" with-temp-message))) (custom-set-faces '(default ((t (:background "black" :foreground "#137D11"))))) (require 'init-startup) (require 'init-generic) (require 'lazycat-theme) (require 'cache-path-from-shell) (require 'lazy-load) (require 'one-key) (require 'awesome-pair) (require 'display-line-numbers) (require 'basic-toolkit) (require 'redo) (require 'highlight-parentheses) (require 'init-awesome-tray) (require 'init-awesome-tab) (require 'init-backup) (require 'init-line-number) (require 'init-auto-save) (require 'init-mode) (require 'init-dired) (require 'init-session) (require 'init-awesome-pair) (require 'init-indent) (require 'init-one-key) (require 'init-key) (require 'init-vi-navigate) (require 'init-performance) (require 'init-pyim) (require 'init-sdcv) (run-with-idle-timer 1 nil (function (lambda nil (require 'pretty-lambdada) (require 'browse-kill-ring) (require 'elf-mode) (require 'init-tempbuf) (require 'init-eldoc) (require 'init-yasnippet) (require 'init-company-mode) (require 'init-smooth-scrolling) (require 'init-cursor-chg) (require 'init-winpoint) (require 'init-info) (require 'init-atomic-chrome) (require 'init-c) (require 'init-flycheck) (require 'init-idle) (require 'init-auto-sudoedit) (require 'init-highlight-indent-guides) (emacs-session-restore))))) (and with-temp-message (if current-message (message "%s" current-message) (message nil))))))
  eval-buffer(#<buffer  *load*-337837> nil "/Users/tomtsang/lazycat-emacs/site-lisp/config/init.el" nil t)  ; Reading at buffer position 2320
  load-with-code-conversion("/Users/tomtsang/lazycat-emacs/site-lisp/config/init.el" "/Users/tomtsang/lazycat-emacs/site-lisp/config/init.el" nil t)
  require(init)
```

也就是，在下面文件里有

`/Users/tomtsang/lazycat-emacs/site-lisp/extensions/cache-path-from-shell/cache-path-from-shell.el`

## (可跳过) 补条件

但是，`grep exec-path-from-shell -rl ./` 发现，有好多文件都调用到了这个呀，总不能全都注释吧。

还是要想办法解决问题...

参考：

- https://github.com/syl20bnr/spacemacs/issues/3920
- https://github.com/purcell/exec-path-from-shell/issues/34
- https://github.com/purcell/exec-path-from-shell/pull/79

一顿瞎操作如下. 主要是在 最后的 `require(init)` 之前，加条件。

具体如下：

```
;; exec-path-from-shell
;;(require 'exec-path-from-shell)

;;(when (memq window-system '(mac ns))
;;    (exec-path-from-shell-initialize))

;;(provide 'setup-exec-path-from-shell)

;;(setq exec-path-from-shell-arguments '("-i"))
;;(setq exec-path-from-shell-shell-name "bash")

;;(defmacro ignore-warn (&rest body)
;;  (declare (debug t) (indent 0))
;;  `(cl-letf (((symbol-function 'warn) #'ignore))
;;     ,@body))
;;(ignore-warn
;;  (exec-path-from-shell-copy-env "PATH"))
```

好像，也没有什么用。

## cache-path-from-shell

cn.bing.com 搜索 `exec-path-from-shell 安装 emacs` 找到 王勇写的 [cache-path-from-shell, 只加载环境变量一次](https://manateelazycat.github.io/emacs/2018/09/19/cache-path-from-shell.html) 。看一下。最关键的点是：

- cache-path-from-shell 建立一个缓存机制, 确保 exec-path-from-shell-initialize 命令只能执行一次, 从而避免多个 Emacs 插件调用 exec-path-from-shell-initialize 命令而叠加的延时和不爽.
- 从 [cache-path-from-shell](https://github.com/manateelazycat/cache-path-from-shell) 下载 cache-path-from-shell.el ,然后在 ~/.emacs 的最开头的位置加上(注意一定是最开头的位置)

所以，我们要做的就是：

- 下载 [cache-path-from-shell](https://github.com/manateelazycat/cache-path-from-shell) 和 [exec-path-from-shell](https://github.com/purcell/exec-path-from-shell) 包至一个位置，加至 load-path
- cache-path-from-shell 加载 exec-path-from-shell
- 把配置写到 `~/.emacs.d.lazycat-emacs/init.el` 中
  （事后，你会发觉，在`~/.emacs.d.lazycat-emacs/init.el`中不加载`cache-path-from-shell`也是可以的，但是，我们还是加载吧)

### 下载 exec-path-from-shell

```bash
mkdir -p ~/elisp/
git clone https://github.com/purcell/exec-path-from-shell ~/elisp/exec-path-from-shell/
```

### 下载 cache-path-from-shell

```bash
mkdir -p ~/elisp/
git clone https://github.com/manateelazycat/cache-path-from-shell ~/elisp/cache-path-from-shell/
```

### cache-path-from-shell 加载 exec-path-from-shell

`(add-to-list 'load-path (expand-file-name "~/elisp/exec-path-from-shell/"))` 加在 `(require 'exec-path-from-shell)` 上一行。如下：

```bash
;;; Require
(add-to-list 'load-path (expand-file-name "~/elisp/exec-path-from-shell/"))
(require 'exec-path-from-shell)
```

原因是，lazycat-emacs 的包，都是在本地，手工加载的。

### 改造 `~/.emacs.d.lazycat-emacs/init.el` 的第二部分

也就是 把 site-start.el 的部分, 加上 `(require 'cache-path-from-shell)` 条件。
同样的原因，要在 `(require 'cache-path-from-shell)` 前加载下载的文件，必须是 `cache-path-from-shell.el`所在的目录。

```
(add-to-list 'load-path (expand-file-name "~/elisp/cache-path-from-shell"))
(require 'cache-path-from-shell)
```

具体如下：

```
;;; Dependencies

(add-to-list 'load-path (expand-file-name "~/elisp/cache-path-from-shell"))
(require 'cache-path-from-shell)

(defun add-subdirs-to-load-path (dir)
  "Recursive add directories to `load-path'."
  (let ((default-directory (file-name-as-directory dir)))
    (add-to-list 'load-path dir)
    (normal-top-level-add-subdirs-to-load-path)))
;;(add-subdirs-to-load-path "/usr/share/emacs/lazycat/")
(add-subdirs-to-load-path "~/lazycat-emacs-3/site-lisp/")

(require 'init)
```

**注意** 我这里的配置文件夹，修改成了 `~/lazycat-emacs-3/site-lisp/`, 这说明了，这个配置文件夹，放在哪里都是可以的。

然后启动，就正常了。
