# 一、说明

> pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
>
> 目前如果你在 [python.org](https://www.python.org/) 下载最新版本的安装包，则是已经自带了该工具。
>
> Python 2.7.9 + 或 Python 3.4+ 以上版本都自带 pip 工具。

## 1.1参考资料

| 名称            | 地址                                                         |
| --------------- | ------------------------------------------------------------ |
| 菜鸟教程pip讲解 | [点击跳转](https://www.runoob.com/w3cnote/python-pip-install-usage.html) |
|                 |                                                              |



# 二、安装

##  2.1检查版本

- 打开命令提示工具win+r  输入cmd打开提示工具

* 输入一下代码查看你的pip版本

```shell
pip --version
```

# 三、切换镜像源(阿里云镜像)

> 1.pip是一个python的管理工具pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
>
>  但是一般用pip下载python的时候使用的是国外的镜像很容易被墙，所以我们这里换成阿里云的镜像
>
> 2.打开你电脑的 C:\Users\你个人的用户目录 新建pip文件夹然后在pip文件夹中建立pip.ini
>
> 创建目录如图所示



![img](https://yaoliuyang-blog-images.oss-cn-beijing.aliyuncs.com/blogImages/1922055-20200822155741995-69061909.jpg)

- 文件右键用记事本打开文件然后在文件中输入

```shell
[global] 
index-url = http://mirrors.aliyun.com/pypi/simple/ 
[install] 
trusted-host=mirrors.aliyun.com
```

ps:然后保存即可，如果电脑不让你保存说你权限不够的话你可以在桌面建立之后拉到系统个人目录的pip文件夹中

- 效果如图所示

 ![如图所示](https://yaoliuyang-blog-images.oss-cn-beijing.aliyuncs.com/blogImages/ASjshfNGHY26g3P.jpg)