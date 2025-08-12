#  相对路径无法执行成功

## **错误示例**

> 例如以下业务 我需要读取 **data.txt** 文件内的内容进行数据读取操作   结果执行
>
> python代码后显示报错信息为**File not found: data.txt**

```python
file_path = 'data.txt'
```

## **修改后的代码**

> 给出绝对路径 让程序知道文件在那个位置
>
> [os.path 官方文档](https://docs.python.org/zh-cn/3/library/os.path.html#os.path.realpath)

```python
import os

# 获取当前脚本的目录
script_dir = os.path.dirname(os.path.abspath(__file__))

# 构建文件的绝对路径
file_path = os.path.join(script_dir, 'data.txt')

print(script_dir)
print(file_path)

# 显示结果为
D:\Desktop\py_demo
D:\Desktop\py_demo\data.txt
```

# 为什么我的python文件名 叫pywifi.py 然后文件中导入import pywifi 会报错

>  当你在 Python 文件中尝试导入一个模块时，Python 解释器会在指定的路径下查找该模块。如果你的文件名为 pywifi.py 并且在同一目录下尝试导入 pywifi，会出现以下问题：
>
>  - 命名冲突：当你将文件命名为 pywifi.py 时，Python 解释器会优先查找当前目录下的 pywifi.py 文件而不是你可能想要导入的第三方库 pywifi。
>
>  - 导入错误：由于解释器找到了当前目录下的 pywifi.py 而不是期望的库，这会导致导入错误或程序行为不符合预期。
>
>  为了避免这个问题，你可以采取以下措施之一：
>
>  - 更改文件名：将文件重命名为其他名称，避免与你想导入的模块名相同。
>
>  - 使用完整路径导入：如果必须保留文件名，可以尝试使用更具体的导入方式，例如通过修改 sys.path 来明确指定第三方库的位置。
>
>  例如，如果你确实需要保留文件名 pywifi.py，并且想导入同一环境中的 pywifi 库，可以通过调整 sys.path 来实现：

```python
import sys
# 假设 pywifi 库安装在 site-packages 中
sys.path.append('/path/to/site-packages')
import pywifi
```

> 但最简单的方法还是更改文件名以避免冲突。