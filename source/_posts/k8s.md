---
title: Ubuntu下搭建Kubernetes + Docker环境
date: 2020-2-18
tags: 
- Kubernetes
- Docker
- Helm
---

在Ubuntu环境下搭建Kubernetes管理的Docker集群

- Ubuntu下Docker的安装 [Get Docker Engine - Community for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
- Kubernetes的安装：实验环境下我们使用Microk8s
- Kubernetes的安装：实验环境下我们使用MiniKube [Install Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)

### 踩坑--网络问题

#### Docker换源

```json
{
  "registry-mirrors": [
    "http://registry.docker-cn.com",
    "http://docker.mirrors.ustc.edu.cn"
  ],
  "insecure-registries": [
    "registry.docker-cn.com",
    "docker.mirrors.ustc.edu.cn"
  ]
}
```

#### 阿里云镜像安装k8s

```bash
apt-get update && apt-get install -y apt-transport-https
```

```bash
curl https://mirrors.aliyun.com/kubernetes/apt/doc/apt-key.gpg | apt-key add -
```

向`/etc/apt/sources.list.d/kubernetes.list`中添加

```bash
deb https://mirrors.aliyun.com/kubernetes/apt/ kubernetes-xenial main
```

```bash
apt-get update
apt-get install -y kubelet kubeadm kubectl
```
