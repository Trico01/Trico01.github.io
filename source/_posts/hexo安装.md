---
title: hexo安装
date: 2021-04-22 09:45:03
tags:
- note
---
基本安装方法在hexo及主题的文档里说的已经很清晰了，非常好用，难度不大。

**安装步骤：**
按照hexo文档建站->修改基本配置->按照theme的文档进行安装、修改->按照hexo文档部署到github page。

**主要说明以下问题：**
1. 本地运行
启动Hexo Server进行本地预览时，在站点根目录执行下述命令
```
hexo s --debug
```
其中`--debug`参数不加也行，加了能看到详细信息，但用处不大（我几乎没用上），跑的还慢。
2. 部署到github page
在hexo文档中写的很详细。使用git（我用的是fork，但现在好像付费了）推送站点文件夹即可。每次更改文件后网页更新得很慢，大概3~5min，如果网页没有立即变化的话也不要担心。
3. 图片上传
使用hexo-asset-image组件。很奇怪的是在node_modules里虽然有该组件，但文件里写的东西跟图片上传驴唇不对马嘴（反正我看不懂），所以重新安装一下：
站点根目录执行
```
npm install https://github.com/CodeFalling/hexo-asset-image -- save
```
更改站点配置文件_config.yml中
```
post_asset_folder: true
```
此时用`hexo new "<文章名>"`新建文章后，在_posts下会出现同名的文件夹和.md文件，将欲上传的图片放在文件夹下，在.md中使用`![<图片标注>](<图片名称>.jpg)`即可上传。

**踩过的坑：**
* 安装组件时一定要挂上vpn，而且是全局模式！因为用了跳过中国节点找了一下午的bug...
* 组件文档里说的`npm install hexo-asset-image --save`并不好使，应该是版本有更新过。