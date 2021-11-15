# linux源码-编译安装

## 资料

| 名称                | 地址                                                        |
| ------------------- | ----------------------------------------------------------- |
| 菜鸟教程-python安装 | [link](https://www.runoob.com/python3/python3-install.html) |
|                     |                                                             |

## 安装

**[官网下载](https://www.python.org/downloads/source/)**

<img src="https://i.loli.net/2021/11/15/bw58NDtmzaZyKVj.png" alt="1636944911(1).jpg" style="zoom:50%;" />

推荐[淘宝镜像npm](https://npm.taobao.org/mirrors)下载 

```shell
# 地址
https://npm.taobao.org/mirrors/python/
```



- 下载

```shell
# wget 下载
wget https://npm.taobao.org/mirrors/python/3.9.8/Python-3.9.8.tgz
# curl 下载
curl -o Python-3.9.8.tgz   https://npm.taobao.org/mirrors/python/3.9.8/Python-3.9.8.tgz
# 为了方便
```

- [安装](https://www.cnblogs.com/smilevv/p/14134901.html)

```shell
tar -zxvf Python-3.9.8.tgz
cd Python-3.9.8
./configure   --prefix=/usr/local/python3.9
make && sudo make install
```

查看是否安装成功

```shell
php --version
# 如果没有指定目录的时候 默认安装目录
[root@iZuf69knglysgxpotcmkn1Z python3.9]# pwd
/usr/local/lib/python3.9
# 全局使用python3命令
[root@iZuf69knglysgxpotcmkn1Z]# python3 --version      
Python 3.9.8
# 查看pip 
[root@101fe8e80378 /]# pip3 --version
pip 21.2.4 from /usr/local/lib/python3.9/site-packages/pip (python 3.9)
```



## 卸载

**编译安装卸载**

```shell
sudo rm -rf  /usr/local/python
```

**卸载centos自带python**

> 发现centos自带python尝试卸载发现报错**Error: Trying to remove "yum", which is protected（错误:试图删除yum，它是受保护的）**
>
> 参考[资料](https://www.pythonf.cn/read/7183)

```shell
 yum remove python # 无法卸载
 # rpm -e 表示卸载rpm包  --nodeps忽略依赖关系的卸载
 rpm -e --nodeps python 
```



# windows安装

>点击`Downloads`=>`Windows`

<img src='https://yaoliuyang-blog-images.oss-cn-beijing.aliyuncs.com/blogImages/1922055-20201015113456373-96008708.png' width='600px' heigth='400px' title='官网'>

>下载安装程序

<img src='https://yaoliuyang-blog-images.oss-cn-beijing.aliyuncs.com/blogImages/1922055-20201015113829489-1600403853.png' width='600px' heigth='400px' title='下载程序'>

## 安装

`记得勾选` ==path==

<img src='https://yaoliuyang-blog-images.oss-cn-beijing.aliyuncs.com/blogImages/1922055-20201015113910212-399442107.jpg' width='600px' heigth='400px' title='安装'>

## 测试

>使用cmd输入`python`然后输出命令测试即可

<img src='https://yaoliuyang-blog-images.oss-cn-beijing.aliyuncs.com/blogImages/1922055-20201015114052532-325243859.png' width='600px' heigth='400px' title='测试'>

## 更改镜像查看我的另一篇博客[pip切换阿里云镜像（国内镜像）](https://www.cnblogs.com/yaoliuyang/p/12505441.html)

# pip安装

> pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
>
> 目前如果你在 [python.org](https://www.python.org/) 下载最新版本的安装包，则是已经自带了该工具。
>
> Python 2.7.9 + 或 Python 3.4+ 以上版本都自带 pip 工具。

## 参考资料

| 名称                   | 地址                                                         |
| ---------------------- | ------------------------------------------------------------ |
| 菜鸟教程pip讲解        | [点击跳转](https://www.runoob.com/w3cnote/python-pip-install-usage.html) |
| 菜鸟教程-pip安装-linux | [点击跳转](Python pip 安装与使用)                            |

## 安装

### linux安装



## 切换镜像源

### windows切换镜像源(阿里云镜像)

> 1.pip是一个python的管理工具pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
>
> 但是一般用pip下载python的时候使用的是国外的镜像很容易被墙，所以我们这里换成阿里云的镜像
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