---
layout: post
title: Github + Vuepress + Travis-CI
category: 技术
tags: "Github Travis-CI Vuepress"
keywords: Github Travis-CI Vuepress
published: true
---

# Travis CI

<img src="https://raw.githubusercontent.com/AlvinMi/2019-Pic/master/2019/20190322193626.jpeg"/>

之前接触了持续集成、持续交付、持续部署的概念。

开始硬着理解，并没有什么收获，挺痛苦的，今天再尝试用一下，Travis CI 结合自己写的`[Dev-Notes](https://github.com/AlvinMi/Developer-notes)`笔记，于是就有了 Github + Vuepress + Travis CI 的组合。

选择 [Travis CI](https://github.blog/2017-11-07-github-welcomes-all-ci-tools/) 的原因是它的使用份额算是比较大的一个，只支持 Github，并且对于开源项目免费，之前在公司看到是使用 Jenkins。

Travis 网上教程应该还是很多的。

## 使用

访问 [travis-ci](https://travis-ci.org/first_sync), 使用 Github 账号登录，会出现所有的仓库和所属的组织。

右边会有开关一样的按钮，打开就等于激活了，Travis 就会监听这个仓库的变化。

添加 `.travis.yml` 文件到项目根目录下，Travis-CI 会按照该文件里的内容进行构建。

因为每次写完笔记后，都需要先 push, 然后自己在本地 build 将 Markdown 转换成页面，再把页面 push 到仓库的 gh-pages 分支。

持续集成就帮忙省去了 push 之后的这些事情，例如在一些 Github 仓库看到 `.travis.yml` 文件就是这个意思了。

## Travis.yml 文件

我的项目是 `.travis.yml` 文件是这样的:

```yml
language: node_js
node_js:
  - "8.15.1"

cache:
  directories:
    - "node_modules"

branches:
  only:
    - dev

install:
  - npm install
  - npm run build

script:
  - ./deploy.sh

# deploy:
#   provider: pages
#   skip-cleanup: true
#   github-token: $GITHUB_ACCESS_TOKEN  # Set in travis-ci.org dashboard, marked secure https://docs.travis-ci.com/user/deployment/pages/#Setting-the-GitHub-token
#   target-branch: gh-pages
#   local-dir: .vuepress/dist
#   on:
branch: dev
```

由于 Vuepress 官方已经给了部署的脚本例子，就不多说了，Travis 里面还是用这个脚本。也就是说当 push 或者 pr 到自己的仓库时， travis 会自动去执行这个 `deploy.sh`。

并不是就这么完了，还需要 Github 的权限，需要去 [Github Setting](https://github.com/settings/tokens) 生成一个 Personal access tokens。

复制这个 token 到 Travis 后台所在的仓库，在环境变量(Environment Variables) 设置键值对，Add 的时候前面自己定一个值，需要在后面用到。

这样 Travis 就有能访问 github 仓库的权限了，最后一步，需要修改 `deploy.sh`，把里面的:

```bash
git push -f git@github.com:AlvinMi/Developer-notes.git master:gh-pages
```

改为：

```bash
git push -f https://${填自己 Travis 后台设置的值}@github.com/AlvinMi/Developer-notes.git master:gh-pages
```

试着 push，再看看 Travis 后台有没有成功。

中间也遇到了一些小坑，例如 Travis 部署后 vuepress 不能正常显示，原因我是部署在 `gh-pages`， 需要设置 `config.js`里面的 base，vuepress 文档已经说明；又例如部署失败，原因就是 access-token 设置的时候需要细心。不过都是能解决的，网上搜索找找原因，问题不大。

>代码仓库参考： https://github.com/AlvinMi/Developer-notes