
emacs some display setup

## date, menu-bar, tool-bar, scroll-bar, inhibit-startup-message, highlight line

https://blog.csdn.net/u010654583/article/details/73920206

```elisp
  ;; https://blog.csdn.net/u010654583/article/details/73920206
  ;; I. 显示时间
  ;; .emacs加上：
  (display-time-mode 1) ;; 常显
  (setq display-time-24hr-format t) ;;格式
  (setq display-time-day-and-date t) ;;显示时间、星期、日期

  ;; II. 隐藏菜单栏工具栏滚动条
  ;; .emacs加上：
  (tool-bar-mode 0)
  (menu-bar-mode 0)
  (scroll-bar-mode 0)
  ;;注: 新版改成使用0，旧版使用nil的做法已失效，但 (set-scroll-bar-mode nil) 仍可使用

  ;; III. 关闭启动画面
  ;; .emacs加上：
  (setq inhibit-startup-message t)

  ;; IV. highlight当前行
  ;; .emacs加上：
  (global-hl-line-mode 1)
```


