ubuntu 首次安装 lazycat

# git clone
因为从github下载的时候, 会比较慢,我们选择 github 下载加速.
# git submodule update --init --recursive

```bash
[15:21:14] a:lazycat-emacs git:(master.ubuntu) $ git submodule update --init --recursive
Submodule 'Indium' (https://github.com/NicolasPetton/Indium) registered for path 'site-lisp/extensions/Indium'
Submodule 'auto-save' (https://github.com/manateelazycat/auto-save.git) registered for path 'site-lisp/extensions/auto-save'
Submodule 'aweshell' (https://github.com/manateelazycat/aweshell.git) registered for path 'site-lisp/extensions/aweshell'
Submodule 'awesome-pair' (https://github.com/manateelazycat/awesome-pair.git) registered for path 'site-lisp/extensions/awesome-pair'
Submodule 'awesome-tab' (https://github.com/manateelazycat/awesome-tab.git) registered for path 'site-lisp/extensions/awesome-tab'
Submodule 'awesome-tray' (https://github.com/manateelazycat/awesome-tray.git) registered for path 'site-lisp/extensions/awesome-tray'
Submodule 'site-lisp/extensions/benchmark-init' (https://github.com/dholm/benchmark-init-el) registered for path 'site-lisp/extensions/benchmark-init'
Submodule 'bison' (https://github.com/manateelazycat/bison.git) registered for path 'site-lisp/extensions/bison'
Submodule 'cache-path-from-shell' (https://github.com/manateelazycat/cache-path-from-shell.git) registered for path 'site-lisp/extensions/cache-path-from-shell'
Submodule 'color-rg' (https://github.com/manateelazycat/color-rg.git) registered for path 'site-lisp/extensions/color-rg'
Submodule 'company-english-helper' (https://github.com/manateelazycat/company-english-helper.git) registered for path 'site-lisp/extensions/company-english-helper'
Submodule 'company-lsp' (https://github.com/tigersoldier/company-lsp.git) registered for path 'site-lisp/extensions/company-lsp'
Submodule 'company-tabnine' (https://github.com/TommyX12/company-tabnine.git) registered for path 'site-lisp/extensions/company-tabnine'
Submodule 'css-sort' (https://github.com/manateelazycat/css-sort.git) registered for path 'site-lisp/extensions/css-sort'
Submodule 'delete-block' (https://github.com/manateelazycat/delete-block.git) registered for path 'site-lisp/extensions/delete-block'
Submodule 'duplicate-line' (https://github.com/manateelazycat/duplicate-line.git) registered for path 'site-lisp/extensions/duplicate-line'
Submodule 'site-lisp/extensions/emacs-application-framework' (https://github.com/manateelazycat/emacs-application-framework.git) registered for path 'site-lisp/extensions/emacs-application-framework'
Submodule 'emacs-async' (https://github.com/jwiegley/emacs-async.git) registered for path 'site-lisp/extensions/emacs-async'
Submodule 'emacs-rails' (https://github.com/manateelazycat/emacs-rails.git) registered for path 'site-lisp/extensions/emacs-rails'
Submodule 'emacs-rime' (https://github.com/DogLooksGood/emacs-rime.git) registered for path 'site-lisp/extensions/emacs-rime'
Submodule 'flex' (https://github.com/manateelazycat/flex.git) registered for path 'site-lisp/extensions/flex'
Submodule 'flycheck-pycheckers' (http://github.com/msherry/flycheck-pycheckers) registered for path 'site-lisp/extensions/flycheck-pycheckers'
Submodule 'flycheck-swift' (http://github.com/swift-emacs/flycheck-swift.git) registered for path 'site-lisp/extensions/flycheck-swift'
Submodule 'site-lisp/extensions/fuz' (https://github.com/cireu/fuz.el.git) registered for path 'site-lisp/extensions/fuz'
Submodule 'ghub-plus' (https://github.com/vermiculus/ghub-plus.git) registered for path 'site-lisp/extensions/ghub-plus'
Submodule 'goto-line-preview' (https://github.com/jcs090218/goto-line-preview.git) registered for path 'site-lisp/extensions/goto-line-preview'
Submodule 'grep-dired' (https://github.com/manateelazycat/grep-dired.git) registered for path 'site-lisp/extensions/grep-dired'
Submodule 'highlight-indent-guides' (https://github.com/DarthFennec/highlight-indent-guides.git) registered for path 'site-lisp/extensions/highlight-indent-guides'
Submodule 'highlight-matching-tag' (https://github.com/manateelazycat/highlight-matching-tag.git) registered for path 'site-lisp/extensions/highlight-matching-tag'
Submodule 'iedit' (https://github.com/victorhge/iedit) registered for path 'site-lisp/extensions/iedit'
Submodule 'insert-translated-name' (https://github.com/manateelazycat/insert-translated-name.git) registered for path 'site-lisp/extensions/insert-translated-name'
Submodule 'instant-rename-tag' (https://github.com/manateelazycat/instant-rename-tag.git) registered for path 'site-lisp/extensions/instant-rename-tag'
Submodule 'js2-refactor' (https://github.com/magnars/js2-refactor.el.git) registered for path 'site-lisp/extensions/js2-refactor'
Submodule 'json-reformat' (https://github.com/gongo/json-reformat.git) registered for path 'site-lisp/extensions/json-reformat'
Submodule 'lazy-load' (https://github.com/manateelazycat/lazy-load.git) registered for path 'site-lisp/extensions/lazy-load'
Submodule 'lazy-search' (https://github.com/manateelazycat/lazy-search.git) registered for path 'site-lisp/extensions/lazy-search'
Submodule 'lazycat-theme' (https://github.com/manateelazycat/lazycat-theme.git) registered for path 'site-lisp/extensions/lazycat-theme'
Submodule 'lsp-mode' (https://github.com/emacs-lsp/lsp-mode.git) registered for path 'site-lisp/extensions/lsp-mode'
Submodule 'site-lisp/extensions/magit' (https://github.com/magit/magit) registered for path 'site-lisp/extensions/magit'
Submodule 'site-lisp/extensions/magithub' (https://github.com/vermiculus/magithub) registered for path 'site-lisp/extensions/magithub'
Submodule 'move-text' (https://github.com/manateelazycat/move-text.git) registered for path 'site-lisp/extensions/move-text'
Submodule 'multi-term' (https://github.com/manateelazycat/multi-term.git) registered for path 'site-lisp/extensions/multi-term'
Submodule 'names' (https://github.com/Malabarba/names.git) registered for path 'site-lisp/extensions/names'
Submodule 'nox' (https://github.com/manateelazycat/nox.git) registered for path 'site-lisp/extensions/nox'
Submodule 'olivetti' (https://github.com/rnkn/olivetti.git) registered for path 'site-lisp/extensions/olivetti'
Submodule 'open-newline' (https://github.com/manateelazycat/open-newline.git) registered for path 'site-lisp/extensions/open-newline'
Submodule 'posframe' (https://github.com/tumashu/posframe.git) registered for path 'site-lisp/extensions/posframe'
Submodule 'projectile' (https://github.com/bbatsov/projectile.git) registered for path 'site-lisp/extensions/projectile'
Submodule 'rcodetools' (http://github.com/rcodetools/rcodetools) registered for path 'site-lisp/extensions/rcodetools'
Submodule 'restclient.el' (https://github.com/pashky/restclient.el.git) registered for path 'site-lisp/extensions/restclient.el'
Submodule 'rjsx-mode' (https://github.com/felipeochoa/rjsx-mode.git) registered for path 'site-lisp/extensions/rjsx-mode'
Submodule 'sdcv' (https://github.com/manateelazycat/sdcv.git) registered for path 'site-lisp/extensions/sdcv'
Submodule 'site-lisp/extensions/shift-number' (https://github.com/alezost/shift-number.el.git) registered for path 'site-lisp/extensions/shift-number'
Submodule 'sly-el-indent' (https://github.com/cireu/sly-el-indent.git) registered for path 'site-lisp/extensions/sly-el-indent'
Submodule 'smart-align' (https://github.com/manateelazycat/smart-align.git) registered for path 'site-lisp/extensions/smart-align'
Submodule 'snails' (https://github.com/manateelazycat/snails.git) registered for path 'site-lisp/extensions/snails'
Submodule 'swift-mode' (http://github.com/swift-emacs/swift-mode) registered for path 'site-lisp/extensions/swift-mode'
Submodule 'swiper' (https://github.com/abo-abo/swiper.git) registered for path 'site-lisp/extensions/swiper'
Submodule 'symbol-overlay' (https://github.com/wolray/symbol-overlay.git) registered for path 'site-lisp/extensions/symbol-overlay'
Submodule 'thing-edit' (https://github.com/manateelazycat/thing-edit.git) registered for path 'site-lisp/extensions/thing-edit'
Submodule 'tide' (https://github.com/ananthakumaran/tide.git) registered for path 'site-lisp/extensions/tide'
Submodule 'site-lisp/extensions/transient' (https://github.com/magit/transient.git) registered for path 'site-lisp/extensions/transient'
Submodule 'typescript' (https://github.com/ananthakumaran/typescript.el.git) registered for path 'site-lisp/extensions/typescript'
Submodule 'site-lisp/extensions/unicode-escape' (https://github.com/kosh04/unicode-escape.el.git) registered for path 'site-lisp/extensions/unicode-escape'
Submodule 'vi-navigate' (https://github.com/manateelazycat/vi-navigate.git) registered for path 'site-lisp/extensions/vi-navigate'
Submodule 'watch-other-window' (https://github.com/manateelazycat/watch-other-window.git) registered for path 'site-lisp/extensions/watch-other-window'
Submodule 'web-mode' (https://github.com/fxbois/web-mode) registered for path 'site-lisp/extensions/web-mode'
Submodule 'site-lisp/extensions/with-editor' (https://github.com/magit/with-editor.git) registered for path 'site-lisp/extensions/with-editor'
Submodule 'xr' (https://github.com/mattiase/xr.git) registered for path 'site-lisp/extensions/xr'
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/Indium'...
error: RPC failed; curl 18 transfer closed with outstanding read data remaining
fatal: The remote end hung up unexpectedly
fatal: early EOF
fatal: index-pack failed
fatal: clone of 'https://github.com/NicolasPetton/Indium' into submodule path '/home/a/lazycat-emacs/site-lisp/extensions/Indium' failed
Failed to clone 'site-lisp/extensions/Indium'. Retry scheduled
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/auto-save'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/aweshell'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/awesome-pair'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/awesome-tab'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/awesome-tray'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/benchmark-init'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/bison'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/cache-path-from-shell'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/color-rg'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/company-english-helper'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/company-lsp'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/company-tabnine'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/css-sort'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/delete-block'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/duplicate-line'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/emacs-application-framework'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/emacs-async'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/emacs-rails'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/emacs-rime'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/flex'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/flycheck-pycheckers'...
warning: redirecting to https://github.com/msherry/flycheck-pycheckers/
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/flycheck-swift'...
warning: redirecting to https://github.com/swift-emacs/flycheck-swift.git/
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/fuz'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/ghub-plus'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/goto-line-preview'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/grep-dired'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/highlight-indent-guides'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/highlight-matching-tag'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/iedit'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/insert-translated-name'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/instant-rename-tag'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/js2-refactor'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/json-reformat'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/lazy-load'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/lazy-search'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/lazycat-theme'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/lsp-mode'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/magit'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/magithub'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/move-text'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/multi-term'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/names'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/nox'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/olivetti'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/open-newline'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/posframe'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/projectile'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/rcodetools'...
warning: redirecting to https://github.com/rcodetools/rcodetools/
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/restclient.el'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/rjsx-mode'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/sdcv'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/shift-number'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/sly-el-indent'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/smart-align'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/snails'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/swift-mode'...
warning: redirecting to https://github.com/swift-emacs/swift-mode/
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/swiper'...
error: RPC failed; curl 18 transfer closed with outstanding read data remaining
fatal: the remote end hung up unexpectedly
fatal: early EOF
fatal: index-pack failed
fatal: clone of 'https://github.com/abo-abo/swiper.git' into submodule path '/home/a/lazycat-emacs/site-lisp/extensions/swiper' failed
Failed to clone 'site-lisp/extensions/swiper'. Retry scheduled
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/symbol-overlay'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/thing-edit'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/tide'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/transient'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/typescript'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/unicode-escape'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/vi-navigate'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/watch-other-window'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/web-mode'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/with-editor'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/xr'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/Indium'...
Cloning into '/home/a/lazycat-emacs/site-lisp/extensions/swiper'...
Submodule path 'site-lisp/extensions/Indium': checked out '59f12cb1bc73bb399e00b2c6c69d21bdcb9c0955'
Submodule path 'site-lisp/extensions/auto-save': checked out '405cd13920ee8c199eddec144d6bed3b813caf6e'
Submodule path 'site-lisp/extensions/aweshell': checked out '5c0c2b4f56f511fd329c8fb0e112fa0e1c6264a9'
Submodule path 'site-lisp/extensions/awesome-pair': checked out 'db07cd187ab7f3884a388fb22b424a5a5549393d'
Submodule path 'site-lisp/extensions/awesome-tab': checked out 'b7df83cbf45a1a0a5537bc3fa75a1a15c2932418'
Submodule path 'site-lisp/extensions/awesome-tray': checked out 'cbf241d88f2a3f5ee11df0edad482752fae1ce87'
Submodule path 'site-lisp/extensions/benchmark-init': checked out '7a0f263282bbc86b01b662636306f22813082647'
Submodule path 'site-lisp/extensions/bison': checked out 'e36c2900071229cb6ee916c797c57a3500b4fcfc'
Submodule path 'site-lisp/extensions/cache-path-from-shell': checked out '2a577d407e9609489d404a23a978f1b2f6491086'
Submodule path 'site-lisp/extensions/color-rg': checked out '22b050fc0b9b8d13f10c5fbd4cf14980d2831dc8'
Submodule path 'site-lisp/extensions/company-english-helper': checked out '2341279fde7c4fb8004da09aa75f8cd6807e8d69'
Submodule path 'site-lisp/extensions/company-lsp': checked out 'f921ffa0cdc542c21dc3dd85f2c93df4288e83bd'
Submodule path 'site-lisp/extensions/company-tabnine': checked out 'a207f493eaf1cc766eb25ae84d0eca4c9d3e433b'
Submodule path 'site-lisp/extensions/css-sort': checked out '2023551efbfb9a5ab99da82f343247e5db8b7d7f'
Submodule path 'site-lisp/extensions/delete-block': checked out '50e1df3e273ffa049525726fb72818e859ecc9cf'
Submodule path 'site-lisp/extensions/duplicate-line': checked out '5abe4b81fa1618212938eb2e9b153975c34c11f1'
fatal: remote error: upload-pack: not our ref 03970628cb3f8d5e65f05a068ed27ef8ced43431
Fetched in submodule path 'site-lisp/extensions/emacs-application-framework', but it did not contain 03970628cb3f8d5e65f05a068ed27ef8ced43431. Direct fetching of that commit failed.
[19:13:18] a:lazycat-emacs git:(master.ubuntu*) $

```

这一步之后, `./site-lisp/extensions/lazycat-theme`下是没有文件的.
# git submodule foreach git reset --hard

```
[10:20:47] a:lazycat-emacs git:(master.ubuntu*) $ git submodule foreach git reset --hard
Entering 'site-lisp/extensions/Indium'
HEAD is now at 59f12cb Merge branch 'nodejs-program-args' of nico/Indium into master
Entering 'site-lisp/extensions/auto-save'
HEAD is now at 405cd13 Merge pull request #5 from han1475/master
Entering 'site-lisp/extensions/aweshell'
HEAD is now at 5c0c2b4 Merge pull request #55 from LittleJianCH/master
Entering 'site-lisp/extensions/awesome-pair'
HEAD is now at db07cd1 Make `awesome-pair-wrap-round' and `awesome-pair-equal' works with script area of html file.
Entering 'site-lisp/extensions/awesome-tab'
HEAD is now at b7df83c Don't render left margin when disable icon.
Entering 'site-lisp/extensions/awesome-tray'
HEAD is now at cbf241d Just show origin message if got any error, easy to debug.
Entering 'site-lisp/extensions/benchmark-init'
HEAD is now at 7a0f263 readme: Simple elisp for el-get installation
Entering 'site-lisp/extensions/bison'
HEAD is now at e36c290 Highlight comment block.
Entering 'site-lisp/extensions/cache-path-from-shell'
HEAD is now at 2a577d4 Add exec-path-from-shell in readme.
Entering 'site-lisp/extensions/color-rg'
HEAD is now at 22b050f Add new command `color-rg-insert-current-line'.
Entering 'site-lisp/extensions/company-english-helper'
HEAD is now at 2341279 Merge pull request #7 from EvanMeek/master
Entering 'site-lisp/extensions/company-lsp'
HEAD is now at f921ffa Allow completion in strings and comments
Entering 'site-lisp/extensions/company-tabnine'
HEAD is now at a207f49 Merge pull request #30 from kisaragi-hiu/patch-1
Entering 'site-lisp/extensions/css-sort'
HEAD is now at 2023551 Fix duplicate attribute issue: https://github.com/manateelazycat/css-sort/issues/1
Entering 'site-lisp/extensions/delete-block'
HEAD is now at 50e1df3 Add subword depend.
Entering 'site-lisp/extensions/duplicate-line'
HEAD is now at 5abe4b8 first commit
Entering 'site-lisp/extensions/emacs-application-framework'
HEAD is now at 199a9aa Notifies user to use eaf-open-office to open office files
Encountered 23 file(s) that should have been pointers, but weren't:
	app/js-video-player/node_modules/loadjs/examples/assets/flash.png
	app/js-video-player/node_modules/loadjs/test/assets/flash.gif
	app/js-video-player/node_modules/loadjs/test/assets/flash.png
	app/mermaid/node_modules/css-b64-images/draft.png
	app/mermaid/node_modules/css-b64-images/test/fixture/img/background-pattern.gif
	app/mermaid/node_modules/css-b64-images/test/fixture/img/mixit-banner.png
	screenshot/air_share.png
	screenshot/aria2.gif
	screenshot/browser.gif
	screenshot/camera.gif
	screenshot/eaf-interleave.gif
	screenshot/file_browser.png
	screenshot/file_transfer.png
	screenshot/framework.png
	screenshot/image_viewer.gif
	screenshot/markdown_previewer.gif
	screenshot/mermaid.gif
	screenshot/mindmap.gif
	screenshot/org_previewer.gif
	screenshot/pdf_viewer.gif
	screenshot/rss_reader.gif
	screenshot/terminal.gif
	screenshot/video_player.gif
Entering 'site-lisp/extensions/emacs-async'
HEAD is now at 86aef2c Untabify and indent-buffer (#119)
Entering 'site-lisp/extensions/emacs-rails'
HEAD is now at 070f032 Fix string-join conflict with subr-x.el in Emacs.
Entering 'site-lisp/extensions/emacs-rime'
HEAD is now at daf956d add rime-show-preedit variable
Entering 'site-lisp/extensions/flex'
HEAD is now at 03a5dba Handle string syntax highlight.
Entering 'site-lisp/extensions/flycheck-pycheckers'
HEAD is now at dcf5b09 Hack + prepwork for better path typing.
Entering 'site-lisp/extensions/flycheck-swift'
HEAD is now at 4c5ad40 Fix Makefile errors
Entering 'site-lisp/extensions/fuz'
HEAD is now at 0b6b64c chore: Bump version to 1.4.0
Entering 'site-lisp/extensions/ghub-plus'
HEAD is now at b1adef2 Merge pull request #15 from titaniumbones/patch-1
Entering 'site-lisp/extensions/goto-line-preview'
HEAD is now at 1f0afb2 Add stable badge.
Entering 'site-lisp/extensions/grep-dired'
HEAD is now at 1f53289 Delete unused code.
Entering 'site-lisp/extensions/highlight-indent-guides'
HEAD is now at 1b12c7b Added bitmap display method
Entering 'site-lisp/extensions/highlight-matching-tag'
HEAD is now at 2f57d4a Fix error of `highlight-matching-tag-get-close-tag-bound'
Entering 'site-lisp/extensions/iedit'
HEAD is now at 0fb3d38 Set the FIXEDCASE argument of replace-match in iedit-replace-occurrences to T to allow preserving case.
Entering 'site-lisp/extensions/insert-translated-name'
HEAD is now at a11b8f5 Use `default-input-method' instead pyim method.
Entering 'site-lisp/extensions/instant-rename-tag'
HEAD is now at 5909263 Revert "first post"
Entering 'site-lisp/extensions/js2-refactor'
HEAD is now at d4c40b5 Merge pull request #120 from stepnem/fix-custom-declaration
Entering 'site-lisp/extensions/json-reformat'
HEAD is now at 8eb6668 fix README
Entering 'site-lisp/extensions/lazy-load'
HEAD is now at cd98190 Merge pull request #1 from kuxiade/master
Entering 'site-lisp/extensions/lazy-search'
HEAD is now at 15b62a0 Add `lazy-search-to-color-rg'
Entering 'site-lisp/extensions/lazycat-theme'
HEAD is now at f9cea44 Fix load condition error.
Entering 'site-lisp/extensions/lsp-mode'
HEAD is now at 9f24011 [docs] add gdscript missing docs
Entering 'site-lisp/extensions/magit'
HEAD is now at 0e3b8695 magit-abbrev-length: Try harder for find sample commits
Entering 'site-lisp/extensions/magithub'
HEAD is now at 9fb9c65 Merge pull request #403 from mgcyung/transient
Entering 'site-lisp/extensions/move-text'
HEAD is now at 5942268 upgrade doc.
Entering 'site-lisp/extensions/multi-term'
HEAD is now at 017c77c Merge pull request #5 from MatthewZMD/master
Entering 'site-lisp/extensions/names'
HEAD is now at d8baba5 Merge pull request #30 from jabranham/byte-compiler-warns
Entering 'site-lisp/extensions/nox'
HEAD is now at 1293812 Send shutdown message without arguments.
Entering 'site-lisp/extensions/olivetti'
HEAD is now at 2728ee5 Merge pull request #46 from rnkn/visual-line-option
Entering 'site-lisp/extensions/open-newline'
HEAD is now at 640cce7 first commit
Entering 'site-lisp/extensions/posframe'
HEAD is now at ee6457a Merge pull request #62 from ericdallo/patch-1
Entering 'site-lisp/extensions/projectile'
HEAD is now at 5103cfc Add a changelog entry for the performance improvement done in #1528
Entering 'site-lisp/extensions/rcodetools'
HEAD is now at 70e1689 Merge pull request #32 from fobo66/patch-1
Entering 'site-lisp/extensions/restclient.el'
HEAD is now at ac8aad6 Add back jq IP example
Entering 'site-lisp/extensions/rjsx-mode'
HEAD is now at 0061587 Merge pull request #122 from nikolas/patch-1
Entering 'site-lisp/extensions/sdcv'
HEAD is now at 8ee62a7 Merge pull request #14 from loyalpartner/master
Entering 'site-lisp/extensions/shift-number'
HEAD is now at cd099a5 Add Makefile
Entering 'site-lisp/extensions/sly-el-indent'
HEAD is now at e1b4ea7 refactor: Move `flet` series into same of cl-aliasing.
Entering 'site-lisp/extensions/smart-align'
HEAD is now at 4435953 first commit
Entering 'site-lisp/extensions/snails'
HEAD is now at 72085df Merge pull request #59 from loyalpartner/master
Entering 'site-lisp/extensions/swift-mode'
HEAD is now at 2ab9ea1 Bump version to 8.0.2
Entering 'site-lisp/extensions/swiper'
HEAD is now at 62815d9 Makefile: Compile ivy-avy.el
Entering 'site-lisp/extensions/symbol-overlay'
HEAD is now at 8096a68 Prefer "Rename to" in prompt for symbol renaming
Entering 'site-lisp/extensions/thing-edit'
HEAD is now at 117eadc Fix `thing-replace-region-or-line' no region here error
Entering 'site-lisp/extensions/tide'
HEAD is now at 13e7af7 update tsserver
Entering 'site-lisp/extensions/transient'
HEAD is now at 0cd0b45 transient-define-*: Explicitly use `defun' indentation style
Entering 'site-lisp/extensions/typescript'
HEAD is now at 0fc7297 Add compilation-mode support for ng lint too.
Entering 'site-lisp/extensions/unicode-escape'
HEAD is now at fc69ec7 Add MELPA Stable badge
Entering 'site-lisp/extensions/vi-navigate'
HEAD is now at ee00dd4 Adjust man mode hook name.
Entering 'site-lisp/extensions/watch-other-window'
HEAD is now at d6d28c9 Adjust readme.
Entering 'site-lisp/extensions/web-mode'
HEAD is now at 186a7c2 php indent fix
Entering 'site-lisp/extensions/with-editor'
HEAD is now at 7ec873b Release version 2.9.2
Entering 'site-lisp/extensions/xr'
HEAD is now at 1c4934d Add github auto-test infrastructure
[10:24:12] a:lazycat-emacs git:(master.ubuntu*) $
```
这一步之后, `./site-lisp/extensions/lazycat-theme`下有文件了.
# git submodule foreach git checkout master

```
[10:24:12] a:lazycat-emacs git:(master.ubuntu*) $ git submodule foreach git checkout master
Entering 'site-lisp/extensions/Indium'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/auto-save'
Previous HEAD position was 405cd13 Merge pull request #5 from han1475/master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/aweshell'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/awesome-pair'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/awesome-tab'
Previous HEAD position was b7df83c Don't render left margin when disable icon.
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/awesome-tray'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/benchmark-init'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/bison'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/cache-path-from-shell'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/color-rg'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/company-english-helper'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/company-lsp'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/company-tabnine'
Previous HEAD position was a207f49 Merge pull request #30 from kisaragi-hiu/patch-1
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/css-sort'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/delete-block'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/duplicate-line'
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/emacs-application-framework'
M	screenshot/video_player.gif
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/emacs-async'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/emacs-rails'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/emacs-rime'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/flex'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/flycheck-pycheckers'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/flycheck-swift'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/fuz'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/ghub-plus'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/goto-line-preview'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/grep-dired'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/highlight-indent-guides'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/highlight-matching-tag'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/iedit'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/insert-translated-name'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/instant-rename-tag'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/js2-refactor'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/json-reformat'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/lazy-load'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/lazy-search'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/lazycat-theme'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/lsp-mode'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/magit'
Already on 'master'
Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)
Entering 'site-lisp/extensions/magithub'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/move-text'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/multi-term'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/names'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/nox'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/olivetti'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/open-newline'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/posframe'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/projectile'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/rcodetools'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/restclient.el'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/rjsx-mode'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/sdcv'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/shift-number'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/sly-el-indent'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/smart-align'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/snails'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/swift-mode'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/swiper'
Already on 'master'
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)
Entering 'site-lisp/extensions/symbol-overlay'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/thing-edit'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/tide'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/transient'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/typescript'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/unicode-escape'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/vi-navigate'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/watch-other-window'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/web-mode'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/with-editor'
Already on 'master'
Your branch is up to date with 'origin/master'.
Entering 'site-lisp/extensions/xr'
Already on 'master'
Your branch is up to date with 'origin/master'.
[10:27:12] a:lazycat-emacs git:(master.ubuntu*) $
```


# install pyqt5

安装过程见文档

# install PyQt related packages

some pyqt related package must install

比如会提示： No module named 'PyQt5.QtWebEngineWidgets'

## install PyQtWebEngine

- version: PyQtWebEngine-5.14.0

```
pip3 install PyQtWebEngine -i https://pypi.tuna.tsinghua.edu.cn/simple
```

# eaf

## eaf download page

when i use `M-x eaf-proxy-insert_or_open_download_manage_page`, show the following error:

```
dbus-call-method: D-Bus error: "Traceback (most recent call last):\n  File \"/usr/lib/python3/dist-packages/dbus/service.py\", line 707, in _message_cb\n    retval = candidate_method(self, *args, **keywords)\n  File \"/usr/share/emacs/lazycat/extensions/emacs-application-framework/eaf.py\", line 326, in execute_function\n    buffer.execute_function(function_name)\n  File \"/home/a/lazycat-emacs/site-lisp/extensions/emacs-application-framework/core/buffer.py\", line 216, in execute_function\n    getattr(self, function_name)()\n  File \"/home/a/lazycat-emacs/site-lisp/extensions/emacs-application-framework/core/browser.py\", line 861, in _do\n    getattr(self, method_name)()\n  File \"/home/a/lazycat-emacs/site-lisp/extensions/emacs-application-framework/core/browser.py\", line 734, in open_download_manage_page\n    self.try_start_aria2_daemon()\n  File \"/home/a/lazycat-emacs/site-lisp/extensions/emacs-application-framework/core/browser.py\", line 731, in try_start_aria2_daemon\n    subprocess.Popen(aria2_args, stdout=null_file)\n  File \"/usr/lib/python3.6/subprocess.py\", line 729, in __init__\n    restore_signals, start_new_session)\n  File \"/usr/lib/python3.6/subprocess.py\", line 1364, in _execute_child\n    raise child_exception_type(errno_num, err_msg, err_filename)\nFileNotFoundError: [Errno 2] No such file or directory: 'aria2c': 'aria2c'\n" [2 times]
```

so install aria2c

```bash
sudo apt install aria2c
```
## eaf open mmd file

`M-x eaf-open *.mmd`

```bash
pip3 install pyinotify markdown
```