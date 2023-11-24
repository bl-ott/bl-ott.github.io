---
layout: post
title: Weekly Study 2023.11.24
---

## 十步学习法

1. 了解全局
2. 确定范围
3. 定义目标
4. 寻找资源
5. 创建学习计划
6. 筛选资源
7. 开始学习，浅藏辄止
8. 动手操作，边学边玩
9. 全面掌握，学以致用
10. 乐为人师，融会贯通

（摘自：《软技能：代码之外的生存指南》)


## Facebook的研发效率

Facebook 的研发效能非常高，更是硅谷公司中的一个典范。比如，早在 2012 年 Facebook 月活达到 10 亿的时候，后端服务及前端网站的部署，采用的是每周一次全量代码部署、每天一次增量代码部署，以及每天不定次数的热修复部署，但部署人员就只有三个，达到平均每个部署人员支撑 3.3 亿用户的惊人效率。

社交网络出现 Bug 的时候，调测起来非常麻烦。因为要复现 Bug 场景中错综复杂的社交网络数据，困难并且耗时。但在 Facebook，它采用开发环境跟生产环境共享一套数据的方法。这就使得开发人员可以非常方便地在自己的机器上复现这个 Bug，进行调测。当然，这样的数据共享机制背后有着强大的技术和管理支撑来规避风险。
（摘自：《研发效率破局之道》）

## Git objects

![]({{ site.baseurl }}/images/git-objects.png)
在`.git/objects`中存储了git仓库的对象
包含这些类型：

- commit
- tag
- tree
- blog

我们可以通过`cat-file -t`命令查看object的类型,`cat-file -p`打印输出object

```
git cat-file -t // show object type 
git cat-file -p // pretty-print <object> content
```
（摘自《Git三剑客》）

![1585291432_100883](../images/1585291432_100883.jpeg)
