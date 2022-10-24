---
title: gitee+hexo搭建个人博客
top_img: /imgs/bg2.jpg
# top_img: ./gitee+hexo搭建个人博客/1.png
date: 2020-11-11 17:59:15
tags: [gitee, hexo]
categories:
  - web
  - front-end
---
## Reference
[如何利用好Github pages](https://www.jianshu.com/p/7c013faaaba1)  


## jekyll 的不足

- gitee 上使用 jekyll 效果完全和 Github 上不同，必须要在本地环境编译再 push, 而 github 自带 jekyll 引擎，可以直接在 github 原码上直接修改
- https://www.cnblogs.com/FLY_DREAM/p/13669729.html

## hexo

- 教程https://www.cnblogs.com/yizhixue-hx/p/12638361.html

### hexo init 卡住

https://www.jianshu.com/p/a409601734f1
<!-- ![图片](gitee-hexo搭建个人博客/1.png) -->
![图片](./gitee+hexo搭建个人博客/1.png)

```
hexo init blog
```

换成, (下面 npm 换成 cnpm 更快)

```
git clone --depth 1 https://gitee.com/weilining/hexo-starter.git blog
cd blog
git submodule init
git submodule update
cnpm config set registry http://registry.npm.taobao.org
cnpm i
```

### hexo 插入图片

https://www.jianshu.com/p/f72aaad7b852
https://blog.csdn.net/xjm850552586/article/details/84101345

修改后记得重新生成静态网页

```
hexo clean
hexo generate
hexo server
```

### 生成 ssh 密钥

https://blog.csdn.net/everything1209/article/details/53100263 \*无法识别 ssh-keygen
https://blog.csdn.net/l508742729/article/details/97510883

### 添加公钥位置

https://blog.csdn.net/soulwyb/article/details/90680676

### 自动更新

码云 gitee 搭建 hexo 博客，push 上去之后，page 为什么不能自动更新，得手动更新 page？
gitee pages pro 才支持自动更新

### 解决 hexo 本地与部署不一致问题

更新后如果除臭，一定要清楚浏览器缓存, 可能受之前 url 影响
https://blog.csdn.net/GAI159/article/details/105128186

### 主题

说明：https://www.baidu.com/link?url=0CwgUjWRuzWKaRnSvEuNEW2mvpwEWyS6ExNWIB2mWJkbk4pnyuEy4MMtbW2C-lP8&wd=&eqid=a5c7c3b7000e164e000000035fad28b7

[主题推荐](https://www.zhihu.com/question/24422335)

知乎回答：https://www.zhihu.com/question/24422335/answer/336448834
主题：https://github.com/Molunerfinn/hexo-theme-melody
文档：https://molunerfinn.com/hexo-theme-melody-doc/zh-Hans/#%E7%89%B9%E6%80%A7

部署教程：https://molunerfinn.com/hexo-theme-melody-doc/zh-Hans/quick-start.html#%E5%AE%89%E8%A3%85

更新内容后，直接刷新浏览器，不行的话重新启动服务器再刷新浏览器

### 改个人信息

Author, title
\_config.yml 文件

### categories 怎么用

多级分类

https://www.cnblogs.com/seayxu/archive/2016/01/25/5156669.html

```
title: gitee+hexo
top_img: /imgs/bg1.jpg
date: 2020-11-11 17:59:15
tags: [gitee, hexo]
categories: 
- web
- front-end
```
