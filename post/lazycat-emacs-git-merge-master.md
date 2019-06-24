
与 lazycat 同步更新

## git fork update

同步更新Github上Fork的项目

https://www.jianshu.com/p/8ab6ef7ce5e3

https://baijiahao.baidu.com/s?id=1621872750804681718&wfr=spider&for=pc

https://blog.csdn.net/lz_peter/article/details/77972270

## 本地更新

当 manateelazycat/lazycat-emacs 有更新时，merge新代码

```
git checkout master
git pull origin master
git checkout eiuapp
git pull origin eiuapp
git merge master
git submodule init
git submodule update --remote
```

## 启动

```
emacs --with-profile lazycat
```

### 未找到 benchmark-** 文件

如果出现了 `未找到 benchmark-**` 这样的启动错误, 则是因为, 

```
DESKTOP-APB1HCJ% pwd
/mnt/c/Users/a/lazycat-emacs
DESKTOP-APB1HCJ% cat .gitmodules | grep benchma
[submodule "benchmark-init-el"]
        path = site-lisp/extensions/benchmark-init-el
        url = https://github.com/dholm/benchmark-init-el.git
DESKTOP-APB1HCJ% ls site-lisp/extensions/benchmark-init-el -a
.  ..
DESKTOP-APB1HCJ%
```

这就说明, 代码更新了, 子模块文件未下载. 所以要运行一下 `git submodule init && git submodule update` 命令.

