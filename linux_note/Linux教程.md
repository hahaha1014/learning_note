### Linux目录结构

![img](Linux_note.assets/d0c50-linux2bfile2bsystem2bhierarchy.jpg)

bin (binaries)存放二进制可执行文件

sbin (super user binaries)存放二进制可执行文件

只有root才能访问 etc (etcetera)存放系统配置文件，usr (unix shared resources)用于存放共享的系统资源，home 存放用户文件的根目录，root 超级用户目录，dev (devices)用于存放设备文件，lib (library)存放跟文件系统中的程序运行所需要的共享库及内核模块，mnt (mount)系统管理员安装临时文件系统的安装点，boot 启动 Linux 时使用的一些核心文件，tmp (temporary)用于存放各种临时文件，var (variable)用于存放运行时需要改变数据的文件



### Linux常见命令

1. `ls`列举当前工作目录内容，`ll`详细显示工作目录内容
2. `touch` 创建空文件
3. `pwd`(print working directory)显示当前工作目录
4. `cd`(change directory)切换文件路径；`cd /home` 进入 '/ home' 目录' ；`cd ..` 返回上一级目录 ；`cd ../..` 返回上两级目录 ；`cd ~` 返回用户目录 
5. `mkdir filename`新建目录；`mkdir -p test1/test2/test3/test4`多层目录
6. `rmdir filename`删除空目录
7. `rm filename`删除给定文件；-r 同时删除该目录下的所有文件（recursive）；-f 强制删除文件或目录（force）
8. `cp filename filedirectory`复制文件；-r 递归持续复制
9. `mv filename filedirectory`移动文件；`mv filename newfilename`
10. `cat`(concatenate and print files)在标准输出（监控器或屏幕）上查看文件内容
10. `vim filename`进入文件进行修改
11. `grep`在给定的文件中搜寻指定的字符串。`grep -i` 在搜寻时会忽略字符串的大小写，而`grep -r` 则会在当前工作目录的文件中递归搜寻指定的字符串
12. `unzip` 对gzip文档进行解压
13. `df`查看文件系统中磁盘的使用情况–硬盘已用和可用的存储空间以及其它存储设备
14. `date` 显示系统日期 `date -s "2007-08-03 14:15:00" ` 设置日期和时间
14. `reboot` 重启；`shut down`关机
14. `man ls`显示ls指令手册



`ccmake filedirectory`编译。ON/OFF的可以直接用Enter进行切换，修改完之后而按下c键进行配置。等配置结束后，即可继续`make`指令。



Linux+ctrl快捷键：

~~~
ctrl+alt+t：快速打开终端。
ctrl+a: 光标跳到行首。
ctrl+b: 光标左移一个字母。
ctrl+c: 杀死当前进程。
ctrl+d: 删除光标后一个字符或exit、logout。
ctrl+e: 光标移到行尾。
ctrl+f：向后移一个字符。
ctrl+h: 删除光标前一个字符，同backspace键相同。
ctrl+k: 剪切光标后至行尾的内容。
ctrl+l: 清屏，相当于clear。
Ctrl+p：重复上一次命令。
ctrl+r: 搜索之前的命令历史。多次ctrl+r 会一直向上搜索。
ctrl+u: 剪切光标前至行首间的所有内容。
ctrl+w: 剪切前面的字符至上一个空格处。
ctrl+t: 交换光标位置前的两个字符。
ctrl+y: 粘贴或者恢复上次的删除。
Ctrl+x: 跳回之前移动的原位置。
CTRL+SHIFT+T: 在已开终端打开新的Tab
~~~

### 磁盘管理

df（英文全称：disk full）：列出文件系统的整体磁盘使用量；-h ：以人们较易阅读的 GBytes, MBytes, KBytes 等格式自行显示。`df -h /etc`将 /etc 底下的可用的磁盘容量以易读的容量格式显示

du（英文全称：disk used）：检查磁盘空间使用量

fdisk：用于磁盘分区

 `mount` 磁盘挂载：`mount /dev/hdc6 /mnt/hdc6`挂载到 /mnt/hdc6 

### apt常用命令

- 列出所有可更新的软件清单命令：**sudo apt update**

- 升级软件包：**sudo apt upgrade**

  列出可更新的软件包及版本信息：**apt list --upgradeable**

  升级软件包，升级前先删除需要更新软件包：**sudo apt full-upgrade**

- 安装指定的软件命令：**sudo apt install <package_name>**

  安装多个软件包：**sudo apt install <package_1> <package_2> <package_3>**

- 更新指定的软件命令：**sudo apt update <package_name>**

- 显示软件包具体信息,例如：版本号，安装大小，依赖关系等等：**sudo apt show <package_name>**

- 删除软件包命令：**sudo apt remove <package_name>**

- 清理不再使用的依赖和库文件: **sudo apt autoremove**

- 移除软件包及配置文件: **sudo apt purge <package_name>**

- 查找软件包命令： **sudo apt search <keyword>**

- 列出所有已安装的包：**apt list --installed**

- 列出所有已安装的包的版本信息：**apt list --all-versions**

  

### cpp file 生成可执行二进制文件

- 预处理（pre-processing）// .i 文件

```sh
# -E         仅作预处理（如处理包含的头文件，宏定义等）
# -o <文件>	  输出到 <文件>
g++ -E test.cpp -o test.i
```

- 编译（compiling）// .s 文件

```sh
# -S      编译到汇编语言
# .s file 汇编语言文件
g++ -S test.i -o test.s
```

- 汇编（assembling）// .o 文件（可重定位目标文件）

```sh
# -c 汇编到机器语言的目标代码
g++ -c test.s -o test.o
```

- 链接（linking）// bin 文件（可执行目标文件）

```sh
g++ test.o -o test
# -g 选项告诉 g++ 产生能被 GNU 调试器 GDB 使用的调试信息，使能够调试程序
g++ -g asd.cpp -o asd
# 使用 -O2 优化源代码，并生成可执行文件
g++ -O2 test.cpp -o test

-O  # 基本的优化，会同时减小代码的长度和执行时间
-O0 # 不做优化
-O1 # 基本的优化
-O2 # 除了完成基本的优化外，还进行一些额外的调整工作，比如指令调整等（常用 ！一般选择 -O2 就够了 ！）
-O3 # 包括循环展开和其他一些与处理特性相关的优化工作

# 链接 myTest 库，指定该库所在目录
g++ -L/home/lpj/myLib -lmyTest test.cpp -o test
# 使用 c++11 标准进行编译
g++ -std=c++11 test.cpp -o test
```

### reference

[基于VSCode和CMake实现C/C++开发 | Linux篇_哔哩哔哩](https://www.bilibili.com/video/BV1fy4y1b7TC?spm_id_from=333.999.0.0)

