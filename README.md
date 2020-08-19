# GUI可扩展Cmd  

## 简单介绍  
cmdPlus为主程序  
cmdMainDll为编写扩展dll需要的头文件  
Dll1为简单的关闭按钮扩展dll  
每个文件内的Application为成品  

## 详细信息
### CmdPlus  
主程序Script 为扩展插件(DLL)放入的地方  
插件加载失败则无法启动并返回信息框  
src/bg 为背景图片的位置（可以多个图片随机选择）  

### CmdMainDll  
MainDll必须放在主程序同级目录下用于识别(不可放入Script目录)  
可以自己写更多主程序接口用来给扩展插件使用 默认写了四个接口  
编写格式可以在文件内查看  
void DllFunc 主程序唯一识别作为按钮形式响应函数  
参数 ExeHadle 为GUI图形句柄    
参数 cmdHadle 为命令行句柄  
BOOL DllBtnSee 主程序附加识别(可选实现)  
根据函数返回值确定主程序是否显示该插件的按钮形式  
_如果为FALSE则加载dll后不会以按钮的形式在主程序显示  

### Dll1  
插件文件名则为按钮名称
通过导入MainDll生成的Dll lib 以及 .h 头文件  
实现void DllFunc作为主程序按钮的回调函数  
_必须实现DllFunc作为主程序识别的唯一函数否则主程序无法加载_  
可选则实现 BOOL DllBtnSee 按钮是否可见  
编译后放入主程序Script目录下  

## 待改进
部分中文字符无法识别  
↑↓键无法切换 简单实现了tab补全  
无法输入Ctrl+C  
通过cmd启动命令行exe程序无法获取输入输出  
非正常手段关闭cmd.exe和conhost.exe程序不会结束


## 其他
开发环境 vs2019  
使用库 Qt5.14.0  
系统 Windows10  
软件以及dll均为64位  

突然有了一个念头就做了出来 O(∩_∩)O  
同时也是为了学习dll编程 以及对之前知识的综合使用
