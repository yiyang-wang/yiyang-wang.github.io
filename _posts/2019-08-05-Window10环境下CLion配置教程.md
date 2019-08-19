其实我以前一直是微软的脑残粉，所以写大一点的项目一般都是用Visual Studio的，然后刷题的时候使用vscode。知道某一天，我跑实验算法，用了pycharm，瞬间被圈粉了，果断全家桶走起（哈哈，当然是有点夸张了），反正目前CLion用着感觉还行。下面就进入正文，一方面是给自己的总结，另一方面是可以帮助需要帮助的人。

# CLion配置教程（本教程是在win10环境下的）

## 1. 首先你肯定要下载CLion吧
我们就去jetbrains的官网下载CLion，网址如下：
https://www.jetbrains.com/clion/download/#section=windows
![下载页详情](https://img-blog.csdnimg.cn/20190805200000358.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5NDAyNQ==,size_16,color_FFFFFF,t_70)
接下来就是安装了，一路上没啥问题的，这里提一句，如果你有学校的邮箱，就可以申请jetbrains的免费教育许可证，edu教育邮箱验证一下即可，就可以享受正版软件了。

## 2. 配置编译器

 **2.1 方法一：MinGW**
 首先下载MinGW，[官方下载地址](https://osdn.net/projects/mingw/releases/)，但是有时候下载后有点慢，所以我给出[百度网盘](https://pan.baidu.com/s/1uOuxXCSCAiixa7O4l_0j6A)的下载地址，提取码为4dmt ，下载完成后解压到某个路径下就行。
 然后打开CLion进行配置，
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190805201058130.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5NDAyNQ==,size_16,color_FFFFFF,t_70)
 照着图片进行配置，环境选择MinGW（就是后面的路径是你刚才解压的路径，图片中的是我自己的路径，你的需要按照你的解压路径进行填写），不出意外的话其他都会自动补全的。
 ![MinGW](https://img-blog.csdnimg.cn/20190805201457565.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5NDAyNQ==,size_16,color_FFFFFF,t_70)
如果出现无法检测成功的情况，这时候可以手动填写。
CMake一般会自动选择。
Make路径：

    D:\Program Files\mingw64\bin\mingw32-make.exe

C Compiler路径：

    D:\Program Files\mingw64\bin\gcc.exe

C++ Compiler路径：

    D:\Program Files\mingw64\bin\g++.exe

Debugger一般会自己填入，如果没有的话填写：

    D:\Program Files\mingw64\bin\gdb.exe
基本上第一种方法到此结束了。

 **2.2 方法二：Visual Studio**
 我的电脑上就安装了Visual Studio，其实CLion是可以检测到的，直接在Environment中选择Visual Studio即可。
![Visual Studio](https://img-blog.csdnimg.cn/20190805202055800.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5NDAyNQ==,size_16,color_FFFFFF,t_70)
 如果配置成功了，红色箭头旁边的绿色run会亮的。
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190805202426326.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NTQ5NDAyNQ==,size_16,color_FFFFFF,t_70)
 配置的过程就是这些。
 **各位要一起加油哦！**