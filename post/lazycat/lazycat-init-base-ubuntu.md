ubuntu 首次安装 lazycat 后的第一次配置修改

# font

- https://github.com/manateelazycat/lazycat-emacs/issues/17
- https://github.com/manateelazycat/lazycat-theme/blob/6d59ca1e01d450beae6603dd786f8e7bd4087826/lazycat-theme.el#L10

`./site-lisp/extensions/lazycat-theme/lazycat-theme.el` change the font:

```
  (setq emacs-font-name "Droid Sans Mono")))
```
to
```
  (setq emacs-font-name "Source Code Pro")))
```

Source Code Pro 可以下载：


```bash
git clone https://github.com/eiuapp/dot-fonts
```

# sdcv

https://github.com/eiuapp/lazycat-emacs/commit/fed153e5a0aafae04d44565c7b5bb10ba478c408

同时，要求在 $HOME/.stardict/dic/ 下，已经有了这些字典文件哟

```bash
$ ls ~/.stardict/dic                                                                                                                                                   ──(Wed,May27)─┘
stardict21shijishuangyukejicidian242      stardict-dictd-jargon-2.4.2               stardict-kdic-ec-11w-2.4.2    stardict-lazyworm-ec-2.4.2  stardict-oxford-gb-formated-2.4.2  stardict-stardict1.3-2.4.2
stardict-21shijishuangyukejicidian-2.4.2  stardict-dictd_www.dict.org_foldoc-2.4.2  stardict-langdao-ce-gb-2.4.2  stardict-ncce-ce-2.4.2      stardict-ProECCE-2.4.2             stardict-xdict-ce-gb-2.4.2
stardict-cdict-gb-2.4.2                   stardict-dictd_www.dict.org_wn-2.4.2      stardict-lazyworm-ce-2.4.2    stardict-ncce-ec-2.4.2      stardict-quick_eng-zh_CN-2.4.2     stardict-xdict-ec-gb-2.4.2
$ 
```
可以下载：


```bash
git clone https://github.com/eiuapp/dot-stardict
```

# (Optional) .gitignore

https://github.com/eiuapp/lazycat-emacs/commit/8b16c68dded61b131353fb8f45bd5fa66719641e

# (Optional) README.eiuapp.md

(Optional)https://github.com/eiuapp/lazycat-emacs/commit/7ae812acc5558babb43d9f1cce9da33c57ec2564

(Optional)https://github.com/eiuapp/lazycat-emacs/commit/83f4dfccf5f9b75c7c35af4c46045bcf4fce72da

# setq frame title and frame icon

https://github.com/eiuapp/lazycat-emacs/commit/873441b7e349998e6f4bb398053d3390fa7bc97e
