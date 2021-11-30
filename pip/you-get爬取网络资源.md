[created_at]:2021-11-30
[author]:yaoliuyang

# 说明

> 突然在网上看见了一个非常不错的**爬虫包** ***you-get*** 是一个小型命令行实用程序，用于从 Web 下载媒体内容（视频、音频、图像），
>
> 以防万一没有其他方便的方法来执行此操作。

## 资料

| 名称                 | 地址                                                         |
| -------------------- | ------------------------------------------------------------ |
| you-get(pip官网地址) | [link](https://pypi.org/project/you-get/)                    |
| 第三方博客参考       | [link](https://blog.csdn.net/ayouleyang/article/details/104090366) |

# 下载&使用

## 下载

```python
pip install you-get
```

**验证是否安装成功** 

```python
# 输入you-get命令验证即可
PS C:\Users\Administrator> you-get
usage: you-get [OPTION]... URL...
A tiny downloader that scrapes the web
```

##  使用

**cmd命令使用**

```python
# 例如我们从网络上下载一个mv
Administrator@PC-20200506AVAU MINGW64 ~/Desktop
$ you-get https://y.qq.com/n/ryqq/mv/g0041btl4tp
Site:       QQ.com
Title:      SNH48《Honor》官方MV
Type:       MPEG-4 video (video/mp4)
Size:       59.91 MiB (62822461 Bytes)

Downloading SNH48《Honor》官方MV.mp4 ...
 100% ( 59.9/ 59.9MB) ├████████████████████████████████████████┤[1/1]    5 MB/s

# 选择下载路径的方式下载   you-get -o [路径]  [视频地址]

PS C:\Users\Administrator> you-get -o G:\ https://y.qq.com/n/ryqq/mv/g0041btl4tp
Site:       QQ.com
Title:      SNH48《Honor》官方MV
Type:       MPEG-4 video (video/mp4)
Size:       59.91 MiB (62822461 Bytes)
Downloading SNH48《Honor》官方MV.mp4 ...
 100% ( 59.9/ 59.9MB) ├████████████████████████████████████████┤[1/1]    5 MB/s
    
# 实际玩法 二维码视频无法打开
# 先草料二维码解析  https://cli.im/deqr 成网址  然后再直接  you-get + j
```

**代码中使用you-get**

# 目前还没有开始研究python代码所以日后补充

