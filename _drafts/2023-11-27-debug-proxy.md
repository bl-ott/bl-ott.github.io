---
layout: post
title: 抓包
---

![下载](../images/%E4%B8%8B%E8%BD%BD.jpeg)

* TOC
{:toc}

## charles

### 安装charles

[charles官网](https://www.charlesproxy.com/)

### charles配置



### 如何抓取https请求

<img src="../images/491cc88b61baf2a14345a2db192bad17.png" alt="image-20230912144034248.png" style="zoom:50%;" />

<img src="../images/7b72a928100db035f83c872a8eecedef.png" alt="截图" style="zoom:50%;" />

### rewrite

### remote



## 手机抓包



## 电视抓包

首先在电视上开启adb调试功能，不同型号的电视开启方式不同

- 天猫魔盒不支持

- 小米盒子在设置-关于-产品型号 按ok键五次，然后设置-账号与安全中，在安全-ADB调试选择允许

  <img src="../images/image-20231127181343995.png" alt="image-20231127181343995" style="zoom: 33%;" />

  然后在mac上通过adb调试电视实现抓包功能


## adb

### mac安装adb


```sh
brew install --cask android-platform-tools
```

### adb命令

- 连接设备安装app

```sh
// 连接盒子
adb connect 盒子ip

// 测试是否连接
adb devices

// 安装软件
adb install  xx.apk

// 覆盖原版本的安装
adb install -r xx.apk
```

- 设置代理抓包

  设置代理

```sh
adb shell settings put global http_proxy 电脑IP:8888
```

​	移除代理

```sh
adb shell settings delete global http_proxy
adb shell settings delete global global_http_proxy_host
adb shell settings delete global global_http_proxy_port
adb reboot 
```

可以在终端设置如下alias

```sh
alias adb-proxy='adb shell settings put global http_proxy'
alias adb-unproxy='tvunproxy(){adb shell settings delete global http_proxy;adb shell settings delete global global_http_proxy_host;adb shell settings delete global global_http_proxy_port;adb reboot;};tvunproxy'
```

然后执行 `adb-proxy ip:8888`设置代理，执行`adb-unproxy`移除代理

- 截图发到电脑

```sh
adb shell screencap -p /sdcard/01.png

adb pull /sdcard/01.png ~/Downloads
```

同样可以设置alias

```sh
alias adb-cap="adb shell screencap -p /sdcard/01.png && adb pull /sdcard/01.png ~/Downloads"
```



### Q&A

- device offline 怎么解决

1.重启adb服务

```sh
adb kill-server

adb start-server
```



2.盒子设置里先关闭adb 再重新开启 

```sh
adb reconnect offline
```

- more than one device/emulator

把模拟器关掉
