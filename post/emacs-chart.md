emacs 与 图

## 手写plantuml 生成图片太爽了啊. 配合reveal.js 直接生成PPT

**来自 `Emacs & Emacsist 技术群` 的 Arthur 的分享**

在准备内部培训材料， 再次感慨，手写plantuml 生成图片太爽了啊。  配合reveal.js 直接生成PPT

![](https://raw.githubusercontent.com/eiuapp/img/master/img/0e650235c19a971041d6aca36b03a3c.png)


这个图的源代码

```
#+begin_src plantuml :cmdline -charset utf-8 :file ./images/ads-roadmap.png

skinparam shadowing false
skinparam arrowthickness 3
skinparam titlefontsize 20
skinparam backgroundcolor #F4F1E0
skinparam componentbackgroundcolor #EF715A
skinparam componentfontcolor white
skinparam componentfontsize 16

title 在线广告演进\n

package "广告类型" #c2d1bb {
  [品牌广告]
  [效果广告]
}

package "广告形式" #c2d1bb {
  [搜索广告]
  [信息流广告]
  [展示广告]
}

package "在线广告演进" #c2d1bb {
  [展示广告\nDisplaying Ads] -right-> [广告网络\nAdvertising Network]
  [广告网络\nAdvertising Network] -right-> [广告交易平台\nAd Exchange]

  [广告交易平台\nAd Exchange] -up-> [需求方平台\nDemand Side Platform]
  [需求方平台\nDemand Side Platform] -right-> [数据管理平台\nData Management Platform]
  [广告交易平台\nAd Exchange] -down-> [供应方平台\nSupply Side Platform]
}

package "演进方向" #c2d1bb {
  [人群售卖] -right-> [标签人群售卖]
  [标签人群售卖] -right-> [个人售卖]
}

[展示广告] -[hidden]- [效果广告]
[效果广告] -[hidden]- [人群售卖]

#+end_src
```

其中
这两行属于黑科技，是用来控制layout的。

```
[展示广告] -[hidden]- [效果广告]
[效果广告] -[hidden]- [人群售卖]
```

