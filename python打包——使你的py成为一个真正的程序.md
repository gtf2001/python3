# python打包——使你的py成为一个真正的程序

## 前言

python的.py文件打包为一个可执行文件常常使用[pyinstaller](https://so.csdn.net/so/search?q=pyinstaller&spm=1001.2101.3001.7020)库进行操作，本文将介绍使用pyinstaller给.py程序打包的两种方法。

## 正题

1.首先，在命令窗口安装pyinstaller包

> pip install pyinstaller

2.打包

打包有两种语法

| 方法                           | 语法                                                      | 注释                                                         |
| :----------------------------- | :-------------------------------------------------------- | :----------------------------------------------------------- |
| 方法1                          | pyinstaller -F -w --icon=“窗口文件图标绝对路径” 文件名.py | 打包为单个exe文件，一般内部包含了依赖库，所以较大            |
| 方法2                          | pyinstaller -D -w --icon=“窗口文件图标绝对路径” 文件名.py | 打包为一个文件夹，其中exe文件在文件夹内部，这样子单个exe文件就比较小 |
| --icon=“D:\icon\demo\贝宝.ico” |                                                           |                                                              |

## 注意事项

1.pyinstaller打包的时候选定一个文件进行打包，可是要我们创建的完整的程序是由多个文件组成的，我们是不是要打包多个呢？其实不是这样的，pyinstaller已经把我们完成这个程序需要的文件都囊括进去了。前提是我们在此之前所有的.py文件在同一目录下，并且资源文件在.py文件指定的位置。

2.打包完之后运行程序会发现先弹出一个console窗口然后在运行程序，如果不想要调试窗口只需要在pyinstaller语句的时候在最末尾添加上--noconsole 即可，eg:pyinstaller -F mycode.py --noconsole       还可以这样pyinstaller -F -w mycode.py （-w就是取消窗口）