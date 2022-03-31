[created_at]:2021-11-30
[author]:yaoliuyang

# 说明

> 突然在网上看见了一个非常不错的**爬虫包** ***you-get*** 是一个小型命令行实用程序，用于从 Web 下载媒体内容（视频、音频、图像），
>
> 以防万一没有其他方便的方法来执行此操作。

## 资料

| 名称                 | 地址                                                         |
| -------------------- | ------------------------------------------------------------ |
| github  you-get 地址 | [link](https://github.com/soimort/you-get)                   |
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

**基本命令**

```shell
# 零  
you-get -h  # 查看帮助信息显示命令
# 一
you-get -i  视频地址  # 查看视频的详细信息

$ you-get -i https://www.bilibili.com/video/BV177411U72d?spm_id_from=333.999.0.0

site:                Bilibili
title:               迪丽热巴狐妖
streams:             # Available quality and codecs
    [ DASH ] ____________________________________
    - format:        dash-flv360  # 视频格式
      container:     mp4
      quality:       流畅 360P
      size:          4.7 MiB (4882115 bytes)
    # download-with: you-get --format=dash-flv360 [URL]

    [ DEFAULT ] _________________________________  # 默认下载的视频格式地址
    - format:        flv360
      container:     flv
      quality:       流畅 360P
      size:          4.7 MiB (4917706 bytes)
    # download-with: you-get --format=flv360 [URL]
    
# 二   
you-get -o  视频地址  #指定下载的地址

# 三
you-get -F 视频格式  视频地址 

$ you-get -F dash-flv360 https://www.bilibili.com/video/BV177411U72d?spm_id_from=333.999.0.0 # 下载 mp4格式视频地址

```



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
# 先草料二维码解析  https://cli.im/deqr 成网址  然后再直接  you-get + 解析的地址
```

**代码中使用you-get**

# 目前还没有开始研究python代码所以日后补充

