---
layout: post
title: OS X下Tomcat的安装和配置				
date: 2015-10-08 18:20:31
modified: 				
category: "JAVA"
tags: ["JAVA", "Tomcat"]
excerpt: "详细讲解Mac下Tomcat的安装和配置"
comments: true
---

升级后新系统后，发现tomcat等应用不能正常使用。原来在OS X El Capitan中，在内核下引入了Rootless机制[(官网介绍)][System Integrity Protection]，以下路径：

* `/System`
* `/bin`
* `/sbin`
* `/usr` (除 `/usr/local`)

均属于Rootless范围，即使root用户无法对此目录有写和执行权限，只有Apple以及Apple授权签名的软件（包括命令行工具）可以修改此目录。

要么思考你这个操作的意义之后，使用其他方式完成你的操作
比如你要改vim的配置，请放在`~/.vim/`中，而不是`/usr/share`这种全局路径
要么关闭Rootless(需要重启，以Recovery分区启动，在Security Configuration中关闭Enforce System Integrity Protection，平时不推荐)

## 安装和配置Tomcat

### 安装JDK 

 Terminal下输入：

 ~~~
 xiaoo_gan@xiaoo-gan:~$ java -version  
 java version "1.8.0_25"
 Java(TM) SE Runtime Environment (build 1.8.0_25-b17)  
 Java HotSpot(TM) 64-Bit Server VM (build 25.25-b02, mixed mode)
 ~~~

 表示已经安装好JDK

### 下载Tomcat

* 下载：[Tomcat下载地址][tomcat]，下载Core：tar.gz即可
* 解压：

~~~
tar xzvf apache-tomcat-X.X.XX.tar.gz 
~~~

* 移动：

~~~
sudo mv ~/Downloads/apache-tomcat-X.X.XX /usr/local
~~~

* 链接：

~~~
sudo rm -f /Library/Tomcat 
sudo ln -s /usr/local/apache-tomcat-7.0.57 /Library/Tomcat
~~~

* 权限：

~~~
sudo chown -R <your_username> /Library/Tomcat
~~~

* 使所有脚本可执行:

~~~
sudo chmod +x /Library/Tomcat/bin/*.sh 
~~~

* 启动服务器：

~~~
/Library/Tomcat/bin/startup.sh
~~~

在浏览器中输入：[http://localhost:8080/][localhost],出现界面，则表示成功配置好了tomcat
* 关闭服务器:

~~~
/Library/Tomcat/bin/shutdown.sh
~~~

[tomcat]: http://tomcat.apache.org/download-70.cgi
[localhost]: http://localhost:8080/
[System Integrity Protection]: https://developer.apple.com/videos/play/wwdc2015-706/