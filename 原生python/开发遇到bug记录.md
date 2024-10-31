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

