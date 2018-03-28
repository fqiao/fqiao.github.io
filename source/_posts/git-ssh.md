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

## Git和SSH keys

Git是一个版本管理系统，意味着，你可以在本地开始自己的修改，你也可以推送自己的修改到其他git服务器。在你推送自己的修改到远程的git服务器时，你需要一个安全的交流通道去共享修改信息。

SSH提供了这种安全策略，允许你去授权远程的Git服务器不需要在每次推送时都输入账号和密码。

<!-- more -->

对于更多关于SSH的信息，建议你去读 [this nice tutorial by DigitalOcean](https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process).

### 检查是否已存在密钥对

在生成新的秘钥对之前，应该先检查是否已经存在一个秘钥对。在任意位置打开一个shell窗口或者Windows的命令行提示符，然后运行如下命令：

**Windows Command Prompt:**
``` bash
type %userprofile%\.ssh\id_rsa.pub
```

**Git Bash on Windows / GNU/Linux / macOS / PowerShell:**
``` bash
cat ~/.ssh/id_rsa.pub
```

如果存在<font color=#ff0000>ssh-rsa</font>文件，表名密钥对存在，可以直接复制到剪切板，**略过**生成新的秘钥对步骤。反之，你应该生成一个新的密钥对，按照接下来的生成新的秘钥对步骤操作.

说明：公开秘钥对的名称也可能如下：
- <font color=#ff0000>id_dsa.pub</font>
- <font color=#ff0000>id_ecdsa.pub</font>
- <font color=#ff0000>id_ed25519.pub</font>

### 生成新的密钥对

1.生成新的密钥对，使用如下命令

**Git Bash on Windows / GNU/Linux / macOS:**
``` bash
ssh-keygen -t rsa -C "your.email@example.com" -b 4096
```

**Windows:**
建议安装git工具

2.接下来会提示输入秘钥对保存路径
如果选择默认路径，不需要再做任何的配置，SSH客户端会自动使用密钥对
如果自定义路径，需要输入一个路径，然后在<font color=#ff0000>.ssh/config</font>文件里配置该路径。(目前还没有试过该情况)

3.接下来会提示输入密码，你可以直接按Enter键略过输入密码
提示：修改秘钥密码请使用<font color=#ff0000>ssh-keygen -p &lt;keyname&gt;</font>.

4.复制秘钥对到剪切板
复制秘钥对使用如下命令：

**macOS:**
``` bash
pbcopy < ~/.ssh/id_rsa.pub
```

**GNU/Linux (requires the xclip package):**
``` bash
xclip -sel clip < ~/.ssh/id_rsa.pub
```

**Windows Command Line:**
``` bash
type %userprofile%\.ssh\id_rsa.pub | clip
```

**Git Bash on Windows / Windows PowerShell:**
``` bash
cat ~/.ssh/id_rsa.pub | clip
```

5.最后粘贴密钥对到Git服务器