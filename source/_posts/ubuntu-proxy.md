---
title: Ubuntu下设置HTTP Proxy
date: 2020-5-1
tags: 
- Ubuntu
- Proxy
---

*以下配置均在Ubuntu18.04下测试可用*

### bash设置HTTP Proxy


### APT设置HTTP Proxy

创建文件`/etc/apt/apt.conf.d/proxy.conf`并添加如下配置

```
Acquire::http::Proxy "http://user:password@proxy.server:port/";
Acquire::https::Proxy "http://user:password@proxy.server:port/";
```

### Snap设置HTTP Proxy

```bash
sudo snap set system proxy.http="http://user:password@proxy.server:port"
sudo snap set system proxy.https="http://user:password@proxy.server:port"
```
