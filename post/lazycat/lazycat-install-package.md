如何在 lazycat-emacs 中安装包，使用包

后续，希望能把个性化的配置，放在另一个仓库中，方便随时能够跟随lazycat的更新。
当lazycat更新时，我们可以同步更新lazycat; 同时，个性化配置，可以单独随时随地更新。

## lazycat-emacs 安装 proxy-mode

## lazycat 安装 vscode-dark-emacs-theme

### (ok) M1: 加到 init.el 中

```
  ;; start use vscode-dark-emacs-theme
  ;; dir: site-lisp/extensions/vscode-dark-emacs-theme
  (add-to-list 'custom-theme-load-path "~/.spacemacs.d/site-lisp/extensions/vscode-dark-emacs-theme/")
  (load-theme 'vscode-dark t)
  ;; end use vscode-dark-emacs-theme
```

加到 init.el 中。

注： init.el 文件，并不在 lazycat 的git仓库管理中

### (ok) M2: 加入到lazycat/site-lisp

修改2处：

- ./site-lisp/config/init-vscode-dark-emacs-theme.el
- ./site-lisp/config/init.el

#### ./site-lisp/config/init-vscode-dark-emacs-theme.el

add a file ~lazycat/site-lisp/config/init-vscode-dark-emacs-theme.el~

```
 ;; start use vscode-dark-emacs-theme
 ;; dir: site-lisp/extensions/vscode-dark-emacs-theme
 ;; (add-to-list 'custom-theme-load-path "~/lazycat-emacs/self/site-lisp/extensions/vscode-dark-emacs-theme/")
 (add-to-list 'custom-theme-load-path "~/bak/self/site-lisp/extensions/vscode-dark-emacs-theme/")
 (load-theme 'vscode-dark t)
 ;; end use vscode-dark-emacs-theme

(provide 'init-vscode-dark-emacs-theme)
```

#### ./site-lisp/config/init.el

在 ~lazycat/site-lisp/config/init.el~ 加入一句 ~(require 'init-vscode-dark-emacs-theme)~ 用于加载配置。

```
    ;; 可以延后加载的
    (run-with-idle-timer
        ...
        ...
        ...
         (require 'init-vscode-dark-emacs-theme)
        ...
        ...
        ...
    )
```

### (ok) M3: ./site-lisp/config/init-0mine.el

把 init-vscode-dark-emacs-theme.el 等文件，放在另一个地方, 方便管理个性化配置文件。

修改几处：

- ./site-lisp/config/init.el
- ./site-lisp/config/init-0mine.el
- self/site-lisp (个性化配置文件)

思路：把所有的个性化配置，都放在 ./site-lisp/config/init-0mine.el 中加载。

#### ./site-lisp/config/init.el

在 ~lazycat/site-lisp/config/init.el~ 加入一句 ~(require 'init-0mine)~ 用于加载配置。

#### ./site-lisp/config/init-0mine.el

新增文件 ~./site-lisp/config/init-0mine.el~

```
(add-to-list 'load-path "~/lazycat-emacs/self/site-lisp/config/")

;; (require 'init-vscode-dark-emacs-theme)

(let (
      ;; 加载的时候临时增大`gc-cons-threshold'以加速启动速度。
      (gc-cons-threshold most-positive-fixnum)
      (gc-cons-percentage 0.6)
      ;; 清空避免加载远程文件的时候分析文件。
      (file-name-handler-alist nil))

  ;; 定义一些启动目录，方便下次迁移修改

  (with-temp-message ""                 ;抹掉插件启动的输出
    ;; (require 'benchmark-init-modes)

    ;; 可以延后加载的
    (run-with-idle-timer
     1 nil
     #'(lambda ()
         ;; (require 'pretty-lambdada)
         (require 'init-vscode-dark-emacs-theme) ;; 使用 vscode-dark-emacs-theme

         ))))

(provide 'init-0mine)
```

#### self/site-lisp (个性化配置文件)

为了开发（快速参考 ~/lazycat-emacs/site-lisp/）方便，我放在了 ~/lazycat-emacs 下，就是 ~/lazycat-emacs/self/site-lisp ,其实可以放在任意位置。

这里我只用 vscode-dark-emacs-theme 作为演示

```shell
$ tree self/site-lisp/ -L 2
self/site-lisp/
├── config
│   └── init-vscode-dark-emacs-theme.el
└── extensions
    ├── vscode-dark-emacs-theme
```

- config/init-vscode-dark-emacs-theme.el

```
 (add-to-list 'custom-theme-load-path "~/lazycat-emacs/self/site-lisp/extensions/vscode-dark-emacs-theme/")
 (load-theme 'vscode-dark t)
 
(provide 'init-vscode-dark-emacs-theme)
```

- extensions/vscode-dark-emacs-theme

git clone https://github.com/ianpan870102/vscode-dark-emacs-theme


### (ok) M4: self/site-lisp/config/init-init.el

把 init-vscode-dark-emacs-theme.el 等文件，放在一个名为 init-init.el 的文件中，并且这个文件在个性化配置文件git仓库中。

修改几处：

- ./site-lisp/config/init.el
- self/site-lisp (个性化配置文件)

#### ./site-lisp/config/init.el

在 ~lazycat/site-lisp/config/init.el~ 加入2句 用于加载配置：

```
    ;; 可以延后加载的
    (run-with-idle-timer
        ...
        ...
        ...
         (add-to-list 'load-path "~/lazycat-emacs/self/site-lisp/config/")
         (require 'init-init)
        ...
        ...
        ...
    )
```
#### self/site-lisp (个性化配置文件)

- self/site-lisp/config/init-init.el

```
(add-to-list 'load-path "~/lazycat-emacs/self/site-lisp/config/")
(let (
      ;; 加载的时候临时增大`gc-cons-threshold'以加速启动速度。
      (gc-cons-threshold most-positive-fixnum)
      (gc-cons-percentage 0.6)
      ;; 清空避免加载远程文件的时候分析文件。
      (file-name-handler-alist nil))

  ;; 定义一些启动目录，方便下次迁移修改

  (with-temp-message ""                 ;抹掉插件启动的输出
    ;; (require 'benchmark-init-modes)

    ;; 可以延后加载的
    (run-with-idle-timer
     1 nil
     #'(lambda ()
         
         (require 'init-vscode-dark-emacs-theme) ;; 使用 vscode-dark-emacs-theme

         ))))

(provide 'init-init)
```