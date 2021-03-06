![img](vim.assets/vi-vim-cheat-sheet-sch.gif)

##### **进入输入或取代的编辑模式**

- i 为从目前光标所在处输入；I 为在目前所在行的第一个非空格符处开始输入
- a 为从目前光标所在的下一个字符处开始输入；A 为从光标所在行的最后一个字符处开始输入
- o 为在目前光标所在的下一行处输入新的一行；O 为在目前光标所在的上一行处输入新的一行
- r 只会取代光标所在的那一个字符一次；R会一直取代光标所在的文字，直到按下 ESC 为止

##### **移动光标的方法**

- h 或光标向左移动一个字符，j下，k上，l右（向下移动 30 行 "30j" ）
- w将光标向后移动一个word的首字符上；比如"3w"将光标向后移动3个words，b将光标向前移动到前一个word的首字符上，e将光标移动到下一个word的最后一个字符
- gg 移动到这个档案的第一行，相当于 1G 啊！ (常用)；123gg移动到123行
- G 移动到这个档案的最后一行(常用)
- CTRL-F向下滚动一整屏，CTRL-B向下滚动一整屏，CTRL-U向上滚动半屏，CTRL-D向下移动半屏
- 0移动到这一行的最前面字符处 (常用)，$移动到这一行的最后面字符处(常用)

##### **搜索替换**

- `/word` 向光标之下寻找一个名称为 word 的字符串。n向后查找，N向前查找
- `?word`向光标之上寻找一个字符串名称为 word 的字符串
- `:1,$s/XXX/YYY/g`，全局用YYY替换XXX
- `:100,102s/XXX/YYY/g`，指定行范围用YYY替换XXX

##### **删除、复制与贴上**

- x向后删除一个字符, X向前删除一个字符，连续删除 10 个字符“10x”。
- dd 删除游标所在的那一整行(常用)， 20dd 删除 20 行
- dw删除一个word，d4w删除4个word
- d1G删除光标所在到第一行的所有数据；dG删除光标所在到最后一行的所有数据
- d$删除游标所在处到该行的最后一个字符；d0删除游标所在处到该行的最前面一个字符
- yy 复制游标所在的那一行(常用)， y20y 复制 20 行
- y1G复制游标所在行到第一行的所有数据；yG复制游标所在行到最后一行的所有数据
- y$复制游标所在处到该行的最后一个字符；y0复制游标所在处到该行的最前面一个字符
- p 为将已复制的数据在光标下一行贴上，P 则为贴在游标上一行
- J删除换行符，即两行合并
- u 复原前一个动作，(常用)
- [Ctrl]+r 重做上一个动作，(常用)
- .重复前一个动作的， 如果你想要重复删除、重复贴上等等动作，按下小数点『.』就好了！ (常用)

##### **指令行的储存、离开等指令**

- **:** 切换到底线命令模式，以在最底一行输入命令

在命令模式下按下:（英文冒号）就进入了底线命令模式，基本的命令有（已经省略了冒号）：

- q 退出程序；q!强制离开不储存档案
- w 保存文件
- wq储存后离开

##### **选择文本**

- Ctrl + v  从光标当前位置开始，选中光标起点和终点所构成的矩形区域，再按一下Ｃtrl + v结束 

- ggVG 选中全部的文本， 其中gg为跳到行首，V选中整行，G末尾

在命令状态下对当前行用== （连按=两次）, 或对多行用20==表示自动缩进从当前行起的下面20行，使用gg=G可对整篇代码进行排版。

##### 分屏

- `vim -o[n] file1 [file2 ...]`，`vim -O[n] file1 [file2 ...]`打开文件分屏，o水平分屏,O垂直分屏;中括号表示可有可无,n分屏的个数、
- `:vs [file2]`垂直分屏，后面不跟文件名是将当前文件垂直分屏；`:sv [file2]`水平分屏
- `:new [newfile]`新建一个水平分屏，如果跟有文件名则会新建一个文件
- `ctrl+w l`把光标移到右边的屏中；`ctrl+w h`把光标移到左边的屏中；`ctrl+w k`把光标移到上边的屏中；`ctrl+w j`把光标移到下边的屏中
- `:only`关闭除当前分屏外的其他分屏；`:ctrl+w q`关闭当前分屏；`:qa`关闭所有分屏

##### **ctag**

- Ctrl + ] // 跳转到光标所在变量、宏、函数的定义处
- Ctrl + T  // 返回到跳转前的位置
- Ctrl + W + ] // 分割当前窗口，并在新窗口中显示跳转到的定义
- Ctrl + O // 返回之前的位置
- :ts // 列出所有匹配的标签
