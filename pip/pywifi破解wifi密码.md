# 资料

| name     | address                                                      |
| -------- | ------------------------------------------------------------ |
| 网络博客 | [link](https://blog.csdn.net/qq_25662827/article/details/122832594) |



# pywifi安装

```python
# 安装pywifi
pip install pywifi
pip install comtypes # 依赖模块安装
```



# 使用pywifi破解wifi密码案例

```python
import pywifi

wifi = pywifi.PyWiFi()

iface = wifi.interfaces()[0]

print(iface)

```





# bug解析

## [ModuleNotFoundError: No module named 'comtypes'](https://jingyan.baidu.com/article/a17d528555e7a0c199c8f261.html)

[![vXNb7V.md.png](https://gitee.com/yaolliuyang/blogImages/raw/master/blogImages/vXNb7V.md.png)](https://imgse.com/i/vXNb7V)

```python
"D:\Program Files\python\python.exe" C:/Users/铺先生技术研发中心/Desktop/demo.py
Traceback (most recent call last):
  File "C:\Users\铺先生技术研发中心\Desktop\demo.py", line 1, in <module>
    import pywifi
  File "D:\Program Files\python\lib\site-packages\pywifi\__init__.py", line 15, in <module>
    from .wifi import PyWiFi
  File "D:\Program Files\python\lib\site-packages\pywifi\wifi.py", line 15, in <module>
    from .iface import Interface
  File "D:\Program Files\python\lib\site-packages\pywifi\iface.py", line 11, in <module>
    from . import _wifiutil_win as wifiutil
  File "D:\Program Files\python\lib\site-packages\pywifi\_wifiutil_win.py", line 12, in <module>
    from comtypes import GUID
ModuleNotFoundError: No module named 'comtypes'

Process finished with exit code 1


# 如果简单运行报出下面这段错误找不到模块 comtypes  安装即可
pip install comtypes
```

