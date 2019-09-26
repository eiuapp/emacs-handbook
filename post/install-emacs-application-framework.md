安装 emacs-application-framework

[emacs-application-framework](https://github.com/manateelazycat/emacs-application-framework)相当好

## 安装

https://github.com/manateelazycat/emacs-application-framework#installation

## D-Bus error: "No connection to bus"

如果报出 `D-Bus error: "No connection to bus"` 则，参考： https://lists.gnu.org/archive/html/help-gnu-emacs/2011-10/msg00232.html

在命令行下，先运行：

```bash
eval `dbus-launch`
export DBUS_SESSION_BUS_ADDRESS
emacs --with-profile spacemacs
```

这样就不会报错了。

## (未解决)core dumped

when you type `M-x eaf-open-browser RET https://news.baidu.com/ RET`, get following information from `*message*` buffer:

```
Opening https://news.baidu.com/ with EAF-browser...
*eaf* aborted (core dumped)
```

https://github.com/manateelazycat/emacs-application-framework/issues/52

