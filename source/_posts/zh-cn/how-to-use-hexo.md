---
title: how to use hexo
date: 2022-10-24 22:02:36
tags:
---
#  how to use hexo
wait for writting...
## plugins
研究中...
### 1. hexo-serer
Hexo 3.0 把服务器独立成了个别模块，您必须先安装 hexo-server 才能使用。
>npm install hexo-server --save

## config

[hexo配置](https://hexo.io/zh-cn/docs/configuration)
## writting

[hexo写作](https://hexo.io/zh-cn/docs/writing)  
new, layout=[post,page,draft]分别生成到不同目录,page与about,categories页面同级
>hexo new [layout] [title]

通过 publish 命令将草稿移动到 source/_posts 文件夹,该命令的使用方式与 new 十分类似，相当于new之后进行modify(layout)
>hexo publish [layout]  [title]
hexo publish post "draft_post"
hexo publish page "draft_page"

在新建文章时，Hexo 会根据 scaffolds 文件夹内相对应的文件来建立文件，(scaffolds文件夹默认有[post.md,page.md,draft.md]三个layout的模板),例如：
>hexo new photo "My Gallery"
