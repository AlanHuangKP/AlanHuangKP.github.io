---
title: 通过ssh连接Windows并使用wsl进行开发 	
published: 2023-01-11 
tags: ["环境配置"]
category: Blog
draft: false 
---


# 1. 两台Windows之间进行内网穿透
我所采用的软件是`蒲公英`访问端，该软件可以组成虚拟局域网，实现内网穿透。

在官网 <https://pgy.oray.com/download/personal/#visitor> 下载好之后，注册账号，使要组网的两台电脑登录同一个账号，即可在软件中互相看到

# 2. 两台Windows之间开启ssh连接

主要参考这篇文章 <https://zhuanlan.zhihu.com/p/111812831>

# 3. Vscode中开启ssh远程

首先在VScode中，下载远程插件

![V0lMMp.png](https://i.imgloc.com/2023/06/02/V0lMMp.png)

重启VScode后左下角会出现远程图标

![V0lacv.png](https://i.imgloc.com/2023/06/02/V0lacv.png)

点击后在选项卡中选择`Connect to Host...`

![V0l1s3.png](https://i.imgloc.com/2023/06/02/V0l1s3.png)

点击`Add New SSH Host`

然后输入`ssh username@youripadress`点击确定即可连接.


# 4. 远程Windows中开启wsl环境

参考我之前的博客:[使用WSL2搭建CUDA环境](https://hernandez-hkp.github.io/2023/01/04/wsl_cuda/ "使用WSL2搭建CUDA环境")在远程主机上搭建好WSL环境。

在上一步中，我们采用VScode ssh到了远程主机上，我们在命令行中输入`wsl`即可进入WSL环境中

至此，我们完成了用ssh访问远程window

# 5. 关于访问wsl文件的问题
我的评价是，代码放Windows里面，再用`/mnt/`去访问，这样wsl中就可看到代码了。