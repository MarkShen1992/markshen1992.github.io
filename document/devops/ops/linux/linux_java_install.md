### Linux系统中JDK安装

---

### 目录

- 安装前准备
- 安装步骤
- 验证JDK是否安装成功



#### 安装前准备

##### Linux系统版本

Linux操作系统是[CentOS](https://www.centos.org/).

可以使用命令`uname -a`来查看系统的版本信息，顺便介绍下`uname`命令的用法。

```shell
[root@localhost /]# uname --help
用法：uname [选项]...
输出一组系统信息。如果不跟随选项，则视为只附加-s 选项。

  -a, --all                     以如下次序输出所有信息。其中若-p 和
                                -i 的探测结果不可知则被省略：
  -s, --kernel-name             输出内核名称
  -n, --nodename                输出网络节点上的主机名
  -r, --kernel-release          输出内核发行号
  -v, --kernel-version          输出内核版本
  -m, --machine         输出主机的硬件架构名称
  -p, --processor               输出处理器类型或"unknown"
  -i, --hardware-platform       输出硬件平台或"unknown"
  -o, --operating-system        输出操作系统名称
      --help            显示此帮助信息并退出
      --version         显示版本信息并退出
      
[root@localhost /]# uname -a
Linux localhost.localdomain 3.10.0-957.el7.x86_64 #1 SMP Thu Nov 8 23:39:32 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

##### [JDK](https://www.oracle.com/technetwork/java/javase/overview/index.html)版本

你可以根据自己的需求选取不同的JDK版本进行安装。我选择的是[JDK8](https://www.oracle.com/technetwork/java/javase/downloads/index.html#JDK8)这个版本。在下载软件包之前要注册一个用户才可以把软件下载下来。

```
-rw-r--r--. 1 root root 186M 10月  8 02:35 jdk-8u231-linux-x64.tar.gz
```

#### 安装步骤

##### 第一步: 将软件cp到路径 /usr/local 下

```
cp jdk-8u231-linux-x64.tar.gz /usr/local
```

##### 第二步: 进入路径 /usr/local, 解压软件包

```
cd /usr/local
tar -zxvf jdk-8u231-linux-x64.tar.gz
```

##### 第三步: 进入软件解压后的文件夹, 使用`pwd`显示Java_Home

```
cd jdk1.8.0_231/
pwd
```

##### 第四步: 使用`vim`编辑器编辑配置文件`/etc/profile`.

```
vim /etc/profile
```

##### 第五步: 在profile文件中`export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE HISTCONTROL`行下面复制下面的代码

```
export JAVA_HOME=/usr/local/jdk1.8.0_231
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$JAVA_HOME/bin:$PATH
```

##### 第六步: 退出并保存

```
Esc
: wq
```

##### 第七步: 重新生效

```
source /etc/profile
```

#### 验证JDK是否安装成功

说到JDK是否安装成功了呢？在命令行中执行下面的命令测试下就好了。

```
[root@localhost /]# java
用法: java [-options] class [args...]
           (执行类)
   或  java [-options] -jar jarfile [args...]
           (执行 jar 文件)
其中选项包括:
    -d32          使用 32 位数据模型 (如果可用)
    -d64          使用 64 位数据模型 (如果可用)
    -server       选择 "server" VM
                  默认 VM 是 server.

    -cp <目录和 zip/jar 文件的类搜索路径>
    -classpath <目录和 zip/jar 文件的类搜索路径>
                  用 : 分隔的目录, JAR 档案
                  和 ZIP 档案列表, 用于搜索类文件。
    -D<名称>=<值>
                  设置系统属性
    -verbose:[class|gc|jni]
                  启用详细输出
    -version      输出产品版本并退出
    -version:<值>
                  警告: 此功能已过时, 将在
                  未来发行版中删除。
                  需要指定的版本才能运行
    -showversion  输出产品版本并继续
    -jre-restrict-search | -no-jre-restrict-search
                  警告: 此功能已过时, 将在
                  未来发行版中删除。
                  在版本搜索中包括/排除用户专用 JRE
    -? -help      输出此帮助消息
    -X            输出非标准选项的帮助
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  按指定的粒度启用断言
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  禁用具有指定粒度的断言
    -esa | -enablesystemassertions
                  启用系统断言
    -dsa | -disablesystemassertions
                  禁用系统断言
    -agentlib:<libname>[=<选项>]
                  加载本机代理库 <libname>, 例如 -agentlib:hprof
                  另请参阅 -agentlib:jdwp=help 和 -agentlib:hprof=help
    -agentpath:<pathname>[=<选项>]
                  按完整路径名加载本机代理库
    -javaagent:<jarpath>[=<选项>]
                  加载 Java 编程语言代理, 请参阅 java.lang.instrument
    -splash:<imagepath>
                  使用指定的图像显示启动屏幕
有关详细信息, 请参阅 http://www.oracle.com/technetwork/java/javase/documentation/index.html。

[root@localhost /]# javac
用法: javac <options> <source files>
其中, 可能的选项包括:
  -g                         生成所有调试信息
  -g:none                    不生成任何调试信息
  -g:{lines,vars,source}     只生成某些调试信息
  -nowarn                    不生成任何警告
  -verbose                   输出有关编译器正在执行的操作的消息
  -deprecation               输出使用已过时的 API 的源位置
  -classpath <路径>            指定查找用户类文件和注释处理程序的位置
  -cp <路径>                   指定查找用户类文件和注释处理程序的位置
  -sourcepath <路径>           指定查找输入源文件的位置
  -bootclasspath <路径>        覆盖引导类文件的位置
  -extdirs <目录>              覆盖所安装扩展的位置
  -endorseddirs <目录>         覆盖签名的标准路径的位置
  -proc:{none,only}          控制是否执行注释处理和/或编译。
  -processor <class1>[,<class2>,<class3>...] 要运行的注释处理程序的名称; 绕过默认的搜索进程
  -processorpath <路径>        指定查找注释处理程序的位置
  -parameters                生成元数据以用于方法参数的反射
  -d <目录>                    指定放置生成的类文件的位置
  -s <目录>                    指定放置生成的源文件的位置
  -h <目录>                    指定放置生成的本机标头文件的位置
  -implicit:{none,class}     指定是否为隐式引用文件生成类文件
  -encoding <编码>             指定源文件使用的字符编码
  -source <发行版>              提供与指定发行版的源兼容性
  -target <发行版>              生成特定 VM 版本的类文件
  -profile <配置文件>            请确保使用的 API 在指定的配置文件中可用
  -version                   版本信息
  -help                      输出标准选项的提要
  -A关键字[=值]                  传递给注释处理程序的选项
  -X                         输出非标准选项的提要
  -J<标记>                     直接将 <标记> 传递给运行时系统
  -Werror                    出现警告时终止编译
  @<文件名>                     从文件读取选项和文件名
```

如果你的结果和上代码块中一样，说明JDK安装成功。

---

[back2index](./../../../../index.html) 

