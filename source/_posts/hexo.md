---
title: Hexo + GitHub Pages + Travis CI
date: {{ date }}
tags: {
  Hexo,
  Travis CI
}
---

具体操作流程参考：
- 建站流程 [Hexo建站](https://hexo.io/zh-cn/docs/setup)
- 利用Travis CI实现自动部署 [将 Hexo 部署到 GitHub Pages](https://hexo.io/zh-cn/docs/github-pages)

# 踩坑

## 建站过程

- `hexo init <project name>` 需要一个空文件夹，可建好后粘贴内容到Git目录下
- 删除未使用主题，否则在部署到github pages时可能引起报错

## Git

源码仅包含以下文件

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

在以Node为模板的.gitignore文件中需要加入
```
public/
db.json
package-lock.json
```

## Travis CI
因为github pages规则的变化，user pages（即以\<user name\>.github.io命名的repo）生成pages文件仅仅只能放在master branch中。

```
User pages must be built from the master branch.
```

因此建立hexo branch作为source code，通过Travis CI部署到master branch下。

具体配置文件如下：
``` yaml
sudo: false
language: node_js
node_js:
  - 10 # use nodejs v10 LTS
cache: npm
branches:
  only:
    - hexo # build hexo branch only
script:
  - hexo generate # generate static files
deploy:
  provider: pages
  skip-cleanup: true
  github-token: $GH_TOKEN
  keep-history: true
  on:
    branch: hexo
  target_branch: master
  local-dir: public
```
