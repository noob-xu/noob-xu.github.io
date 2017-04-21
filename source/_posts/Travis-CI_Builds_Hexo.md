title: 使用 Travis CI 自动部署 Hexo
date: 2017-4-21 19:59:40
categories: linux
tags: 
- Hexo
- GitHub
- Travis CI
---
> 大三学习Python时接触到了 GitHub 。然后知道可以用GitHub Pages 托管 blog ，后面就接触到了 Hexo 这个神器。不过由于生成静态页面需要部署 node.js 环境，不太方便，最后也没能坚持多久。    
最近，想把学习的一些东西记录下来，又看到有方法可以实现 Hexo 自动部署，于是就有了这篇 blog 。

# Travis CI
CI是 `Continuous Integration` 的缩写，持续集成之意。
> 持续集成是一种软件开发实践，每次集成都通过自动化的构建（包括编译，发布，自动化测试）来验证，从而尽早地发现集成错误。

Travis CI 是一个开源的的在线分布式持续集成服务。

# 工作原理
博客是由 Hexo 搭建的，托管到 GitHub Pages 服务上  
每次写完 blog 后 push 到 Github 上，触发 Travis CI 自动构建，构建完成后自动推送到 GitHub Pages 上
静态文件和 Hexo 目录放在同一个仓库的不同分支上  
**master** : 博客的静态文件  
**hexo** : Hexo 环境代码

# 安装 Hexo
我决定将 Hexo 本地环境部署在 Hyper-V 下的一个 Ubuntu Server 虚拟机上

## 安装前提
根据[官方文档](https://hexo.io/zh-cn/docs/)需要安装下列程序：
* [Node.js](https://nodejs.org/)
* [Git](https://git-scm.com/)
* npm

虚拟机里面已经安装过这两个程序，就不用再安装了，下面开始安装 Hexo

## 安装 Hexo
安装好上述三个程序狗即可使用 npm 安装 Hexo
`$ npm install -g hexo-cli`  

# 初始化和配置 Hexo
> 这里其实遇到了很多问题

https://github.com/iissnan/hexo-theme-next/issues/328
http://w4lle.github.io/2016/06/06/Hexo-themes/
http://aoxuis.me/post/2013-08-06-git-subtree


# 启用要构建的项目
反正上面已经把 Hexo 目录 push 到了 Hexo 分支

