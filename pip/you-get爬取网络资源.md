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

[**参考地址**](https://blog.51cto.com/u_15497022/5101282)

```python
import re,sys,you_get,webbrowser
import tkinter as tk
import tkinter.messagebox as msgbox

"""
视频下载类
"""


class DownloadApp:

    # construct
    def __init__(self, width=800, height=200):
        self.w = width
        self.h = height
        self.title = '视频下载助手'
        self.root = tk.Tk(className=self.title)
        self.url = tk.StringVar()
        self.start = tk.IntVar()
        self.end = tk.IntVar()
        self.path = tk.StringVar()
        self.path.set('D:/DownloadApp')

        # define frame
        frame_1 = tk.Frame(self.root)
        frame_2 = tk.Frame(self.root)
        frame_3 = tk.Frame(self.root)
        frame_4 = tk.Frame(self.root)

        # menu
        menu = tk.Menu(self.root)
        self.root.config(menu=menu)
        menu1 = tk.Menu(menu, tearoff=0)
        menu.add_cascade(label='Menu', menu=menu1)
        menu1.add_command(label='about me', command=lambda: webbrowser.open('https://blog.csdn.net/zwx19921215'))
        menu1.add_command(label='exit', command=lambda: self.root.quit())

        # set frame_1
        label1 = tk.Label(frame_1, text='请输入视频链接：')
        entry_url = tk.Entry(frame_1, textvariable=self.url, highlightcolor='Fuchsia', highlightthickness=1, width=35)

        # set frame_2
        s_lable = tk.Label(frame_2, text='起始值：')
        e_lable = tk.Label(frame_2, text='结束值：')
        start = tk.Entry(frame_2, textvariable=self.start, highlightcolor='Fuchsia', highlightthickness=1, width=10)
        end = tk.Entry(frame_2, textvariable=self.end, highlightcolor='Fuchsia', highlightthickness=1, width=10)

        # set frame_3
        label2 = tk.Label(frame_3, text='请输入视频输出地址：')
        entry_path = tk.Entry(frame_3, textvariable=self.path, highlightcolor='Fuchsia', highlightthickness=1, width=35)
        down = tk.Button(frame_3, text='下载', font=('楷体', 12), fg='green', width=3, height=-1,
                         command=self.video_download)

        # set frame_4
        label_desc = tk.Label(frame_4, fg='black', font=('楷体', 12),
                              text='\n注意：支持youtube、twitter、腾讯、爱奇艺、优酷、bilibili等大部分主流网站视频下载、图片下载！')
        label_warning = tk.Label(frame_4, fg='blue', font=('楷体', 12), text='\nauthor:yaoliuyang')

        # layout
        frame_1.pack()
        frame_2.pack()
        frame_3.pack()
        frame_4.pack()
        label1.grid(row=0, column=0)
        entry_url.grid(row=0, column=1)
        s_lable.grid(row=1, column=0)
        start.grid(row=1, column=1)
        e_lable.grid(row=1, column=2)
        end.grid(row=1, column=3)
        label2.grid(row=2, column=0)
        entry_path.grid(row=2, column=1)
        down.grid(row=2, column=2, ipadx=20)
        label_desc.grid(row=3, column=0)
        label_warning.grid(row=4, column=0)

    """

    视频下载

    """

    def video_download(self):
        # 正则表达是判定是否为合法链接
        url = self.url.get()
        path = self.path.get()
        if re.match(r'^https?:/{2}\w.+$', url):
            if path != '':
                msgbox.showwarning(title='警告', message='下载过程中窗口如果出现短暂卡顿说明文件正在下载中！')
                try:
                    sys.argv = ['you-get', '-o', path, url]
                    you_get.main()
                except Exception as e:
                    print(e)
                    msgbox.showerror(title='error', message=e)
                msgbox.showinfo(title='info', message='下载完成！')
            else:
                msgbox.showerror(title='error', message='输出地址错误！')
        else:
            msgbox.showerror(title='error', message='视频地址错误！')

    def center(self):
        ws = self.root.winfo_screenwidth()
        hs = self.root.winfo_screenheight()
        x = int((ws / 2) - (self.w / 2))
        y = int((hs / 2) - (self.h / 2))
        self.root.geometry('{}x{}+{}+{}'.format(self.w, self.h, x, y))

    def event(self):
        self.root.resizable(False, False)

        self.center()

        self.root.mainloop()


if __name__ == '__main__':
    app = DownloadApp()
    app.event()

 ## 可以将代码打包为exe文件    pyinstaller --onefile 程序.py 
```



# 目前还没有开始研究python代码所以日后补充

