
emacs debug

## 我执行一个函数有点慢。我想debug一下，看看到底慢在什么地方。请问下有什么好办法吗？

profiler-start

## 又不小心改挂了，感觉跑去 git 一顿操作还是太复杂了

- 起两个emacs.一个改，一个测不行吗？
- `emacs -dev`, `emacs -qa`, `emacs -prd`
- https://github.com/Malabarba/elisp-bug-hunter/ 其实这个bug-hunter测试能保证你emacs启动各方面没问题
