# lua学习笔记

## 学习环境搭建

```shell
# 电脑配置
uname -a
Linux localhost.localdomain 3.10.0-957.el7.x86_64 #1 SMP Thu Nov 8 23:39:32 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

# 下载 两种方式
wget https://www.lua.org/ftp/lua-5.3.5.tar.gz
curl -R -O http://www.lua.org/ftp/lua-5.3.5.tar.gz

# 解压文件
tar zxf lua-5.3.5.tar.gz

# 编译
make linux test

# 我在安装时后碰见的问题
lua.c:82:31: 致命错误：readline/readline.h：没有那个文件或目录
#include <readline/readline.h>

# 解决方案
yum install libtermcap-devel ncurses-devel libevent-devel readline-devel

# 在执行下面语句
make linux test

# 配置环境变量
vim /etc/profile

# 添加下面配置
export PATH=${PATH}:/root/soft/lua/lua-5.3.5/src

# 重新生效
source /etc/profile

# 在命令行中执行
lua --help
usage: lua [options] [script [args]].
Available options are:
  -e stat  execute string 'stat'
  -l name  require library 'name'
  -i       enter interactive mode after executing 'script'
  -v       show version information
  --       stop handling options
  -        execute stdin and stop handling options
  
luac --help
luac: unrecognized option '--help'
usage: luac [options] [filenames].
Available options are:
  -        process stdin
  -l       list
  -o name  output to file 'name' (default is "luac.out")
  -p       parse only
  -s       strip debug information
  -v       show version information
  --       stop handling options
```

## Hello World程序

- [Lua官方文档](https://www.lua.org/docs.html)
- [Lua教程](https://www.runoob.com/lua/lua-tutorial.html)

```lua
#! lua_helloworld.lua
print("hello world!");
```

`lua lua_helloworld.lua`执行程序。

## Lua编程方式

### 交互式编程

> 在命令行中输入 lua -i 或者直接输入 lua

### 脚本式编程

> 编写一个 *.lua的文件，写完后运行， lua *.lua即可得到运行结果

## Lua的数据类型

