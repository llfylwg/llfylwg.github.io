---
layout: post
title: centos中创建桌面快捷方式
category: blog
description: 原理解析
---
 
##关于Linux系统版本centos中软件桌面快捷方式创建

> 只有懂了原理，才不用死记创建的步骤，这是真理！Please trust me

前提是你已经安装了linux系统，知道该系统一切都是文件。 "/"是根目录，其他的目录都是“/”的子目录。
这里，可以将这些目录看成是window系统中的文件夹。
安装软件时，默认会安装在  `/usr`这个目录下，你也可以自己新建一个目录作为软件的安装目录。**前提是你必须知道你建的目录的绝对路径** 。

##重要的部分在下面：

安装好后，可以通过终端进入启动文件所在的目录，但是每次这样启动都很不方便，所以需要给该程序创建桌面快捷方式，方便启动。原理是，桌面的所有快捷方式都放在`/usr/share/applications`这个目录下。所以你现在有两种方式来创建：
>1. cp 安装目录中的  `软件名.desktop`到`/usr/share/applications`下；
2. 进入`/usr/share/applications`下，touch一个`软件名.desktop`

然后用root用户权限，修改`/usr/share/applications`中后缀名为`.desktop`的权限为可写可执行。
### 对于方式1
`vi xxxx.desktop`进入该文件的内容中，将`Exec=`后边的路径指向你安装目录中程序启动文件，记住是绝对路径。
### 对于方式2
先进入安装目录中的后缀为`.desktop`文件中拷贝内容到`/usr/share/applications`相应的文件中，同方式1修改`Exec=`的路径。

修改完成后，桌面方式进入`/usr/share/applications`，拷贝快捷方式到桌面即可。

刚开始玩linux，如果有错误，欢迎指出！！
