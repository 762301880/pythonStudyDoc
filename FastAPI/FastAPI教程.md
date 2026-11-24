## 资料

[菜鸟教程`FastAPI`文档](https://www.runoob.com/fastapi/fastapi-tutorial.html)

[fastapi中文文档](https://fastapi.tiangolo.com/zh/)

## FastAPI 特点

FastAPI 之所以在 Python Web 框架中脱颖而出，主要得益于以下特点：

| 特点         | 说明                                                         |
| :----------- | :----------------------------------------------------------- |
| **高性能**   | 基于 Starlette 和 Pydantic，性能与 NodeJS 和 Go 相当，是最快的 Python 框架之一 |
| **快速开发** | 开发速度提升约 200%-300%，标准类型声明即可完成数据校验和文档生成 |
| **减少错误** | 减少约 40% 的人为错误，类型系统自动捕获常见问题              |
| **自动文档** | 自动生成交互式 API 文档（Swagger UI 和 ReDoc），无需手动维护 |
| **类型安全** | 基于标准 Python 类型提示，编辑器提供全面的自动补全和错误检查 |
| **异步支持** | 原生支持 async/await，可高效处理 IO 密集型任务               |

## FastAPI 安装与环境配置

### 创建虚拟环境

推荐在虚拟环境中安装 FastAPI，避免与系统 Python 包产生冲突：

> 虚拟环境是 Python 开发的最佳实践。每个项目使用独立的虚拟环境，可以避免不同项目之间的依赖冲突。

```bash
# 创建虚拟环境
$ python -m venv venv

# 激活虚拟环境（macOS/Linux）
$ source venv/bin/activate

# 激活虚拟环境（Windows）
$ venv\Scripts\activate
```

## 安装 FastAPI

使用 pip 安装 FastAPI：

```bash
$ pip install fastapi
```

## FastAPI 第一个应用

确认有没有装 uvicorn

```bash
# 查看当前虚拟环境有没有uvicorn
pip list | findstr uvicorn
# 没有就安装
pip install uvicorn[standard] fastapi
```

创建一个名为 **main.py** 的文件，添加以下代码：

```python
from fastapi import FastAPI

# 步骤1：导入 FastAPI 类
# 步骤2：创建应用实例
app = FastAPI()

# 步骤3：定义路径操作装饰器
# 步骤4：定义路径操作函数
@app.get("/")
async def root():
    # 步骤5：返回响应内容
    return {"message": "Hello World"}
```

启动应用：

```bash
$ uvicorn main:app --reload
```

访问 **http://127.0.0.1:8000**，返回：

```json
{"message": "Hello World"}
```

