# 蓝目训练版策略编写指南

## 1.函数命名约定
指标宏语言(script)编写，为了区分内置静态函数和外部动态加载函数，对函数命名做了一些约定：  
内置函数直接以函数名称开头，比如SIN, MAX,等。  
外挂DLL函数，以关键词“DLL_”和文件名（文件名称限定字幕数字，其它字符不支持）开头，后跟”@”符号与函数，不区分大小写， 比如”dll_file@fourier”，表示dll插件file文件中的函数 fourier。  
外挂PY语言（需安装完整的PYTHON环境），以文件名（文件名称限定字幕数字，其它字符不支持）和关键词“PY_”开头，区分大小写， 比如”py_func@pyfile”，表示启动运行python的pyfile.py这个文件，并运行func这个函数。  
## 2.DLL插件的注册
在策略编辑的窗口，使用“注册DLL”按钮，如下图所示：

![image](https://github.com/blueye-com/algo-plug/blob/master/blueye_photo/%E5%9B%BE%E7%89%871.png)

点击“注册DLL”后，进入如下界面。

![image](https://github.com/blueye-com/algo-plug/blob/master/blueye_photo/%E5%9B%BE%E7%89%872.png)

如上所示，先选择导入一个已经编译测试好好了的DLL文件，导入后如果该文件是一个新的则需要注册全部函数，如果已经注册过，则会自动把原来注册的函数全部列出来。然后对该DLL的函数进行增删维护（如果要修改，可以先删除再增加）。如下图所示：

![image](https://github.com/blueye-com/algo-plug/blob/master/blueye_photo/%E5%9B%BE%E7%89%873.png)

用户添加的函数名称，系统会自动增加前缀, 格式为“DLL_” + 文件名 + “@”函数名，比如刚刚添加了一个名称为Linear_regression的函数，则系统生成的函数全名为：
DLL_ALGO_PLUGIN.DLL@LINEAR_REGRESSION，以后在脚本语言中如果需要使用该函数，则需要书写该全名，这样编译器在编译的时候会自动搜索导向到指定库文件名称的指定函数。

注意，如果导入的文件是一个非法的DLL（接口函数不存在），则会出现如下提示报错，不能通过。

![image](https://github.com/blueye-com/algo-plug/blob/master/blueye_photo/%E5%9B%BE%E7%89%874.png)

添加函数完成以后，点击“保存”按钮，即可实现了注册。
这时候再点击插入函数页面，则会在“外挂插件函数”中看见刚刚添加的这些函数。

![image](https://github.com/blueye-com/algo-plug/blob/master/blueye_photo/%E5%9B%BE%E7%89%875.png)

插件注册完成后，需要重新启动软件，才能生效，这时候打开指标编辑器，点击插入刚刚增加的函数，则会出现颜色变蓝，以及使用说明的浮动信息提示，如下图所示：

![image](https://github.com/blueye-com/algo-plug/blob/master/blueye_photo/%E5%9B%BE%E7%89%876.png)
