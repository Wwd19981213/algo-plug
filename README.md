# 蓝目训练版策略编写指南

1.函数命名约定
指标宏语言(script)编写，为了区分内置静态函数和外部动态加载函数，对函数命名做了一些约定：  
内置函数直接以函数名称开头，比如SIN, MAX,等。  
外挂DLL函数，以关键词“DLL_”和文件名（文件名称限定字幕数字，其它字符不支持）开头，后跟”@”符号与函数，不区分大小写， 比如”dll_file@fourier”，表示dll插件file文件中的函数 fourier。  
外挂PY语言（需安装完整的PYTHON环境），以文件名（文件名称限定字幕数字，其它字符不支持）和关键词“PY_”开头，区分大小写， 比如”py_func@pyfile”，表示启动运行python的pyfile.py这个文件，并运行func这个函数。  
