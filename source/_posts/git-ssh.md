---
title: ssh key的生成，复制
tags:
  - GIT
categories:
  - Tool
thumbnail: 'http://odue27cqx.bkt.clouddn.com/git_2.jpg'
date: 2018-03-26 18:09:52
---

![](http://odue27cqx.bkt.clouddn.com/git_1.jpg)

### Git和SSH keys

Git是一个版本管理系统，意味着，你可以在本地开始自己的修改，你也可以推送自己的修改到其他git服务器。在你推送自己的修改到远程的git服务器时，你需要一个安全的交流通道去共享修改信息。

SSH提供了这种安全策略，允许你去授权远程的Git服务器不需要在每次推送时都输入账号和密码。

<!-- more -->

对于更多关于SSH的信息，建议你去读 [this nice tutorial by DigitalOcean](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process).