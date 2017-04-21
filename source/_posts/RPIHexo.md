title: 树莓派跑起Hexo
date: 2015-10-10 19:05:44
categories: 
- 树莓派
tags: 
- 树莓派 
- Hexo

---
# 配置运行环境
* ## 下载编译Node.js
``` bash
wget https://nodejs.org/dist/v4.1.2/node-v4.1.2.tar.gz
tar zxvf node-v4.1.2.tar.gz
sudo ./configure
make install
```

 *接下来可以干点别的等它编译完成了 *
 
* ## 安装npm
``` bash
sudo apt-get install npm
```

* ## 安装Hexo
``` bash
sudo npm install -g hexo-cli
```

* ## 创建一个站点
``` bash
mkdir hexoblog
cd hexoblog
hexo init #添加一个博客站点
npm install
```

# 启用Hexo站点
* ## 预览Hexo
``` bash
hexo server
```

在浏览器输入http://localhost:4000/
![hexoserver](http://7xnf9d.com1.z0.glb.clouddn.com/hexoserver.jpg)

# 添加主题
* ## 安装主题
``` bash
git clone https://github.com/iissnan/hexo-theme-next themes/next
```

* ## 启用主题
修改你的博客根目录下的_config.yml配置文件中的theme属性，将其设置为pacman。
``` bash
hexo generate #可以简写为hexo g
hexo s #hexo server的简写
```


   



