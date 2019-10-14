
emacs with proxy

# shell proxy

## startup with proxy

```
export https_proxy='http://127.0.0.1:8118'
export http_proxy='http://127.0.0.1:8118'
emacs
```

## proxychain

```
proxychains emacs -sS 192.168.168.137
```

about proxychain, read [this](https://howiezhao.github.io/2018/10/18/proxychains/)

## zilongshanren's shadowsocks-proxy-mode

`M-x shadowsocks-proxy-mode`

# faq

## spacemacs zilongshanren's shadowsocks-proxy-mode

do not work

## why "https://news.qq.com/" can't open?

but `https://news.baidu.com/` can be opened.
