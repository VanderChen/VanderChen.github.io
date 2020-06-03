---
title: Ubuntu相关设置Tips
date: 2020-5-1
updated: {{date}}
tags: 
- Ubuntu
---




_以下配置均在Ubuntu18.04下测试可用_

### bash设置HTTP Proxy

```bash
export http_proxy=http://user:password@proxy.server:port/;
export https_proxy=http://user:password@proxy.server:port/;
```

### APT设置HTTP Proxy

创建文件`/etc/apt/apt.conf.d/proxy.conf`并添加如下配置

```bash
Acquire::http::Proxy "http://user:password@proxy.server:port/";
Acquire::https::Proxy "http://user:password@proxy.server:port/";
```

### Snap设置HTTP Proxy

```bash
sudo snap set system proxy.http="http://user:password@proxy.server:port"
sudo snap set system proxy.https="http://user:password@proxy.server:port"
```

## R

```R
options(repos=structure(c(CRAN="https://mirrors.tuna.tsinghua.edu.cn/CRAN/")))
```
