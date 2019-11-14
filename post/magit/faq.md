

## Error (use-package): magit/:config: Symbol’s value as variable is void: magit-log-arguments

https://github.com/syl20bnr/spacemacs/issues/12193

https://github.com/syl20bnr/spacemacs/issues/12193#issuecomment-529858701

如果是spacemacs, 则更新最新版本的 spacemacs 的 develop 分支就可以了.

## evil-magit

目标: magit-mode 下, 进入 evil 状态, 可以通过 `hjkl` 等上下左右.

在 magit mode 下自动加载 `evil-magit-toggle-text-minor-mode`

```
    (eval-after-load 'magit
      '(progn
             (evil-magit-toggle-text-minor-mode)
             )
```

## Warning (magit): Magit no longer uses Magit-Popup.

(未成功)

```
Warning (magit): Magit no longer uses Magit-Popup.

It now uses Transient.
See https://emacsair.me/2019/02/14/transient-0.1.

However your configuration and/or some third-party package that
you use still depends on the `magit-popup' package.  But because
`magit' no longer depends on that, `package' has removed it from
your system.

If some package that you use still depends on `magit-popup' but
does not declare it as a dependency, then please contact its
maintainer about that and install `magit-popup' explicitly.

If you yourself use functions that are defined in `magit-popup'
in your configuration, then the next step depends on what you use
that for.

* If you use `magit-popup' to define your own popups but do not
  modify any of Magit's old popups, then you have to install
  `magit-popup' explicitly.  (You can also migrate to Transient,
  but there is no need to rush that.)
\ FEDJ
* If you add additional arguments and/or actions to Magit's popups,
  then you have to port that to modify the new "transients" instead.
  See https://github.com/magit/magit/wiki/Converting-popup-modifications-to-transient-modifications

To find installed packages that still use `magit-popup' you can
use e.g. "M-x rgrep RET magit-popup RET RET ~/.emacs.d/ RET".
```

要把所有的 magit-popup 相关联的部分转至 magit/transient.

reference https://github.com/magit/magit/wiki/Converting-popup-modifications-to-transient-modifications

```
  ;; magit-popup
  (magit-define-popup-switch 'magit-log-popup
      ?1 "First parent" "--first-parent")
   ;; transient
  (transient-append-suffix 'magit-log "-A"
     '("-1" "First parent" "--first-parent"))
```

好吧,按这个思路,我们现在试一下.

```
 (magit-define-popup-switch 'magit-push-popup ?u
     "Set upstream" "--set-upstream")
```

则修改成:
```
 (transient-append-suffix 'magit-push "-u"
     '("Set upstream" "--set-upstream"))
```

发现, 没效果, 是不是哪里错了?
