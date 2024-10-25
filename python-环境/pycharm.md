#  PyCharm

## [下载其他版本](https://www.jetbrains.com.cn/pycharm/download/other.html)

[**下载社区版**-PyCharm Community Edition](https://download.jetbrains.com/python/pycharm-community-2024.2.1.exe?_gl=1*1hxao4u*_gcl_au*MTI3NTIwOTI5LjE3MjYxOTI5OTU.*_ga*MjI3NTQ0MjQwLjE3MjYxOTMwMDA.*_ga_9J976DJZ68*MTcyNjE5Mjk5OS4xLjEuMTcyNjE5MzA1My42LjAuMA..)

# 技巧

## pycharm 中文文档

> https://www.jetbrains.com/help/pycharm/2022.3/installation-guide.html

## [Pycharm自动导入模块小技巧](https://www.jqhtml.com/8948.html)

> 写代码得时候 我们需要一个一个得手动导入 对应得模块名称很是麻烦  
>
> 

**设置类自动导入**

> File | Settings | Editor | General | Auto Import
>
> 在 PyCharm 中，确实可以实现自动导入（import）功能，这能帮助开发者提高编码效率。以下是几种实现自动导入的方法：
> 自动提示导入：
> 当你在代码中使用了一个未导入的模块或类时，PyCharm 会自动检测到这一点，并在该位置下方显示一个黄色灯泡图标。
> 点击该图标，选择“Import this name”，PyCharm 将自动为你添加相应的导入语句。
> 设置自动导入：
> 你可以通过设置让 PyCharm 在输入时自动建议导入。进入 File -> Settings（或者 PyCharm -> Preferences 在 macOS 上）。
> 导航到 Editor -> General -> Auto Import。
> 在这里，你可以勾选“Add unambiguous imports on the fly”选项，这样 PyCharm 会在你输入时自动添加明确的导入语句。
> 手动触发导入：
> 如果你已经编写了一段代码并希望一次性解决所有未导入的问题，可以右键点击编辑器中的任意位置，然后选择 Optimize Imports。这将自动整理和添加所需的导入语句。
> 这些功能使得在 PyCharm 中管理导入变得非常方便，有助于保持代码的整洁和可读性。

![image-20241007145902496](https://gitee.com/yaolliuyang/blogImages/raw/master/blogImages/image-20241007145902496.png)

## pycharm同步配置到云端

> 是不是面临过经常换电脑得问题   换了ide之后又要重新配置一下 之前得配置很麻烦
>
> 我们将本地配置到云端之后只需要重新登录一下账号就可以找回之前得配置

## 设置脚本用控制台执行

> 在 PyCharm 中，默认情况下，运行 Python 脚本可能会使用 Python Console 来执行。如果你不希望使用 Python Console 执行脚本，可以进行以下设置：
>
> **修改运行配置：**
>  打开你要运行的脚本。
>  点击右上角的运行配置下拉菜单，选择 Edit Configurations。
>  在弹出的窗口中，找到你当前的运行配置。
>  取消勾选 Run with Python Console 选项。
>
> **创建新的运行配置：**
>  如果你还没有为当前脚本创建运行配置，可以点击 + 按钮，选择 Python。
>  在新创建的配置中，确保 Script path 正确指向你的脚本文件。
>  同样取消勾选 Run with Python Console 选项。
>
> **保存并应用配置：**
>  完成上述设置后，点击 Apply 按钮，然后点击 OK 保存配置。
>
> **运行脚本：**
>  现在你可以通过点击运行按钮或使用快捷键来运行脚本，它将不再使用 Python Console。
>  通过以上步骤，你可以确保在 PyCharm 中运行 Python 脚本时不会使用 Python Console。

![image-20241025144945907](https://gitee.com/yaolliuyang/blogImages/raw/master/blogImages/image-20241025144945907.png)