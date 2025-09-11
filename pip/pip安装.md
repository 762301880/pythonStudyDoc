## 说明

> pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
>
> 目前如果你在 [python.org](https://www.python.org/) 下载最新版本的安装包，则是已经自带了该工具。
>
> **Python 2.7.9 +** 或 **Python 3.4+** 以上版本都自带 pip 工具。

## 参考资料

| 名称                   | 地址                                                         |
| ---------------------- | ------------------------------------------------------------ |
| 菜鸟教程pip讲解        | [点击跳转](https://www.runoob.com/w3cnote/python-pip-install-usage.html) |
| 菜鸟教程-pip安装-linux | [点击跳转](https://www.runoob.com/w3cnote/python-pip-install-usage.html)   [点击跳转](https://www.runoob.com/w3cnote/python-pip-install-usage.html) |

## 安装

### linux安装

```shell
# 先查看pip是否存在
pip  --version
pip3 --version
# 如果你还未安装，则可以使用以下方法来安装 
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py   # 下载安装脚本
sudo python get-pip.py    # 运行安装脚本
```

****

*用哪个版本的 Python 运行安装脚本，pip 就被关联到哪个版本，如果是 Python3 则执行以下命令：*

```shell
sudo python3 get-pip.py    # 运行安装脚本。	

#一般情况 pip 对应的是 Python 2.7，pip3 对应的是 Python 3.x。
```





## 切换镜像源

###   国内镜像源

```bash
清华大学：https://pypi.tuna.tsinghua.edu.cn/simple
阿里云：https://mirrors.aliyun.com/pypi/simple/
豆瓣：https://pypi.douban.com/simple/
```



### windows切换镜像源(阿里云镜像)

> 1.pip是一个python的管理工具pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。
>
> 但是一般用pip下载python的时候使用的是国外的镜像很容易被墙，所以我们这里换成阿里云的镜像
>
> 2.打开你电脑的 C:\Users\你个人的用户目录 新建pip文件夹然后在pip文件夹中建立pip.ini
>
> 创建目录如图所示



![img](https://gitee.com/yaolliuyang/blogImages/raw/master/blogImages/1922055-20200822155741995-69061909.jpg)

- 文件右键用记事本打开文件然后在文件中输入

```shell
[global] 
index-url = http://mirrors.aliyun.com/pypi/simple/ 
[install] 
trusted-host=mirrors.aliyun.com
```

ps:然后保存即可，如果电脑不让你保存说你权限不够的话你可以在桌面建立之后拉到系统个人目录的pip文件夹中

- 效果如图所示

 ![如图所示](https://gitee.com/yaolliuyang/blogImages/raw/master/blogImages/ASjshfNGHY26g3P.jpg)

### [linux切换镜像源](https://developer.aliyun.com/mirror/pypi)

> 首先在用户目录下建立文件
>
> .pip 就是可隐藏文件  可以 ls -a命令显示出来

```shell
sudo mkdir ~/.pip && sudo  touch ~/.pip/pip.conf  # 建立 pip.conf文件
sudo chmod -R 777 pip.conf  # 设置可以编辑权限
vim pip.conf  # 编辑
# 文件中添加以下即可
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/

[install]
trusted-host=mirrors.aliyun.com
```

**直接使用命令设置**

- **`pip config set`**: 修改 pip 的配置。
- **`global.index-url`**: 指定全局的 PyPI 镜像地址。
- **`https://mirrors.aliyun.com/pypi/simple/`**: 阿里云提供的 PyPI 镜像地址（国内访问更快）

```shell
# pip config list
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/

pip install some-package -i https://pypi.tuna.tsinghua.edu.cn/simple
```

**为什么需要这样设置？**

1. **加速下载**：
   - 默认的 PyPI 源（`https://pypi.org/simple/`）在国外，国内直接访问可能较慢或超时。
   - 使用阿里云镜像可以显著提升下载速度。
2. **解决网络问题**：
   - 避免因网络不稳定导致的 `pip install` 失败（如超时、连接中断）。

**生效范围**

- **全局生效**：所有 Python 项目的 `pip install` 命令都会使用该镜像源。
- **配置文件位置**：
  修改后的配置会保存在 pip 的全局配置文件中（路径因系统而异）：
  - Linux/macOS: `~/.config/pip/pip.conf`
  - Windows: `%APPDATA%\pip\pip.ini`

### **其他常用国内镜像源**

如果阿里云镜像不稳定，可以替换为其他源：

```shell
# 清华大学源
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple/

# 腾讯云源
pip config set global.index-url https://mirrors.cloud.tencent.com/pypi/simple/

# 豆瓣源
pip config set global.index-url https://pypi.doubanio.com/simple/
```

### **如何恢复默认源？**

> 或手动删除配置文件中的 `index-url` 行。

```bash
pip config unset global.index-url
```

输出示例：

```shell
global.index-url='https://mirrors.aliyun.com/pypi/simple/'
```

## pip 工具的简单使用

**查看已经安装的包**

> `pip list` 命令列出已经安装的包

```python
yaoliuyang@yaoliuyang-PC:~$ pip list
Package    Version
---------- -------
distro     1.3.0
onboard    1.4.1
pexpect    4.6.0
Pillow     5.4.1
pip        21.3.1
pycairo    1.16.2
PyGObject  3.30.4
pywifi     1.1.12
reportlab  3.5.13
setuptools 59.4.0
wheel      0.37.0
```

**卸载已经安装的软件包**

> `pip uninstall + 包名`

```python
pip uninstall pywifi
```

##  疑问

### pip安装的软件都在那

**windows**

1. 常规全局安装

> 如果没有启用虚拟环境，pip 通常会将软件包安装到 Python 安装目录下的`Lib\site-packages`文件夹中。
>
> 例如，要是 Python 安装在 `C:\Python312`，那么安装包存放路径就是 `C:\Python312\Lib\site-packages` 。

2. 用户目录安装

> 当你用普通用户权限安装，且安装时使用了`--user`参数，
>
> pip 会把软件包安装到用户目录对应的 Python 包存储区，
>
> 具体路径为`C:\Users\用户名\AppData\Roaming\Python\Python版本号\site-packages` 。

3. 虚拟环境内安装

> 要是启用了虚拟环境，pip 安装的软件包会放在虚拟环境目录里的`Lib\site-packages`中 。
>
> 比如，你的虚拟环境建在 “C:\my_venv”，那安装路径即为 “C:\my_venv\Lib\site-packages” 。