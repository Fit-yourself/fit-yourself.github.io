+++
title = "HEXO+GitPage搭建博客"
date = "2018-12-31"
tags = ["Tech","Learn"]
+++

首先向大家展示我的博客：
www.vseelove.top *挺简约的吧？*
工具： ** Git hexo Nodejs **
在元旦前告知需要的虫友们。
以上工具 各位自行受获取【天气冷】
[Git下载界面](https://www.git-scm.com/download/)
[Nodejs下载界面](https://nodejs.org/en/)

## 1.注册Github
 username.github.io 
 ** username是你的注册时信息，非我的。 **
 如果已经有Github，可直接创建仓库.注册于创建时，注意**username**，这关系到你的初始域名，发挥你的创造力。
![join][1]
注册过程可能需要验证你的邮箱，其他就不在赘述。

+ 创建仓库
创建一个仓库(repository) 来存储我们的网站，点击首页任意位置出现的 New repository按钮创建仓库, Respository name 中的username.github.io 的username 一定与前面的Owner 一致，记住你的username下面会用到。
*还有你注册的邮箱*
这是红的因为我已经注册过一次了，
![ku][2]
create~~~OK~！

## 2.安装Git Hexo
+ Git下载后，可直接安装
+ 安装Nodejs
【Hexo是一种博客框架基于Nodejs（其它框架与此不讨论）】

 如此，工具准备好。

## 3.最后一公里 
先用Hexo初始化博客 配置，后发布至个人Github网站【~~username~~.github.io】
**在Git Bash下（其实WIN下的Dos也可以）**
**配置（安装） Hexo**
``npm install -g hexo-cli``
+ 创建本地库
创建出一个名为 username.github.io 的文件夹。
``hexo init username.github.io``
然后进去
``cd username.github.io ``
*初始化的过程是从 hexo 仓库下载博客的目录结构和文件，根据网速，需要一定时间。*

安装依赖模块：
``npm install``

 + 主题安装
    在本地库下
 下进行。【抱歉由于时间的原因，我晚上要考试，明天上学，虫友们可以在下我参考的5分钟里找到相似的。】
 ** 调整基础配置 **

## 然后你就可以愉快的写文章了,后上传。
但你要上传的话，我建议在家的虫友可以** 设置免密提交 **
``cd username.github.io ``

+ 配置 Git 用户名和邮箱
 ``git config --global user.name "username"``
``git config --global user.email"username@mail.com"``
生成密钥
``ssh-keygen -t rsa -C "username@mail.com"``
使用 ssh-agent 管理私钥
在Ssh的文件夹下
``eval "$(ssh-agent -s)"``
将生成的密钥添加到 ssh-agent
``ssh-add id_rsa``
将公钥添加到GitHub中
在网页上登陆Github
在 GitHub 个人的设置中，添加 SSH-KEY。
** 验证 **
``ssh -T git@github.com``
出现如下，就是成功了。
``Hi username! You've successfully authenticated, but GitHub does not provide shell access.``
---
是到了发布的前夕了。
在本地库下
先生成静态页面
``hexo g`` （看有无错误。）
然后本地服务器** 测试 **
``hexo s``
能够正常启动服务器，并在浏览器中访问，说明 Hexo 配置成功，接下来要做的事情就是讲生成的静态页面提交到 Github上即可。

## 提交 Hexo 到 GitHub
修改 _config.yml 文件，在最后增加如下内容：
``deploy:
  type: git
  repository: git@github.com:username/username.github.io.git
  branch: master
``
*注意*“：”后有空格

+ 安装hexo-deployer-git自动部署发布工具
``npm install hexo-deployer-git --save``
发布
测试没问题后，我们就生成静态网页文件发布至我们的Github pages 中。
``hexo clean && hexo g && hexo d``

# 大功告成 
``Hexo g 
hexo s
hexo d
`` 一定要知道是干嘛的。

【手好冷啊！祝大家新年快乐！！！】
（如有不足，请告知。）

---

以下为参考页面：
>[5分钟 搭建免费个人博客](https://www.jianshu.com/p/4eaddcbe4d12)

> [Github Hexo搭建博客](https://weilu2.github.io/2018/09/29/%E5%9F%BA%E4%BA%8EGithub%E7%BB%93%E5%90%88Hexo%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)


[1]: /images/join.jpg
[2]: /images/2.jpg