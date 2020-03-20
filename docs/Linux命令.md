

![](https://img.vim-cn.com/4f/997ad5a19156a30ad1c9c0cecdb8f6f1e65a6e.png)

Shell是一个命令行工具。Shell（也称为终端或壳）充当的 是人与内核（硬件）之间的翻译官，用户把一些命令“告诉”终端，它就会调用相应的程序服务去完成某些工作。现在许多主流Linux系统默认使用的终端是Bash（Bourne-Again SHell）解释器。
![](https://img.vim-cn.com/37/8d7196d9a03975e518d1347c3aed2cbcd9ef4e.png)

![](https://img.vim-cn.com/d8/1adfe8ac8a38361bd55673d693dfdd1430b0ff.png)

### 常用系统工作命令

1. echo
含义：用于在终端输出字符串或变量提取后的值.

```shell
echo hello
hello

echo $SHELL
/bin/bash
```

2. date
date命令用于显示及设置系统的时间或日期,在强大的date命令中输入以“+”号开头的参数，即可按照指定格式来输出系统的时间或日期

```shell
# date
 Mon Aug 24 16:11:23 CST 2017 
# date "+%Y-%m-%d %H:%M:%S" 
2017-08-24 16:29:12 
# date "+%j" 
244 //显示今天是当年当中的第几天
```

3. reboot
reboot命令用于重启系统

4. poweroff
poweroﬀ命令用于关闭系统

5. wget命令 
wget命令用于在终端中下载网络文件，格式为“wget [参数] 下载地址”。 
```shell
# wget -r -p http://www.linuxprobe.com --2017-08-24 19:31:41-- http://www.linuxprobe.com/ Resolving www.linuxprobe.com... 106.185.25.197 Connecting to www.linuxprobe.com|106.185.25.197|:80... connected. HTTP request sent, awaiting response... 200 OK Length: unspecified [text/html] Saving to: 'www.linuxprobe.com/index.html' 

```

6. ps
ps命令用于查看系统中的进程状态，格式为“ps [参数]”。

7. top命令 
top命令用于动态地监视进程活动与系统负载等信息，其格式为top。

8. pidof命令 
pidof命令用于查询某个指定服务进程的PID值，格式为“pidof [参数] [服务名称]”。 
例如，可以使用如下命令来查询本机上sshd服务程序的PID：

```shell
# pidof sshd 
2156 
```

9. kill命令
kill命令用于终止某个指定PID的服务进程，格式为“kill [参数] [进程 PID]”。 

10. killall命令 
killall命令用于终止某个指定名称的服务所对应的全部进程，格式 为：“killall [参数] [进程名称]”。

```shell
# pidof httpd 
13581 13580 13579 13578 13577 13576 
# killall httpd 
# pidof httpd 
# 
```

tip:在系统终端中执行一个命令后想立即停止:Ctrl + C,如果有些命令在执行时不断地在屏幕 上输出信息，影响到后续命令的输入，则可以在执行命令时在末尾添加上一个&符号，这样命令将进入 系统后台来执行。

### 系统状态监检测命令
……部分略……

1. ifconfig
ifconﬁg命令用于获取网卡配置与网络状态等信息，格式为“ifconﬁg [网络设备] [参数]”。

2. history命令 
history命令用于显示历史执行过的命令，格式为“history [-c]”。 能显示最近1000条命令记录。使用-c参数则会清空所有的命令历史记录。

```shell
# history -c
```

### 工作目录切换命令

1. pwd命令 
pwd命令用于显示用户当前所处的工作目录，格式为“pwd [选项]”。

```shell
# pwd 
/etc 
```

2. **cd命令**
cd命令用于切换工作路径，格式为“cd [目录名称]”。 
“cd -”：命令返回到上一次所处的目录，
“cd ..”：命令进入上级目录， 
“cd ~”：命令切换到当前用户的家目录，
“cd ~username”：切换到其他用户的家目录。

3. ls命令 
ls命令用于显示目录中的文件信息，格式为“ls [选项] [文件] ”。 
使用ls命 令的“-a”参数看到全部文件（包括隐藏文件），使用“-l”参数可以查看文 件的属性、大小等详细信息。将这两个参数整合之后，再执行ls命令即可 查看当前目录中的所有文件并输出这些文件的属性信息

tips:
* 隐藏文档一般以 "." 开头；
* "."表示当前路径；
* ".."表示上一级路径
* 使用"ls -la"显示的目录：第一列表示文档类型，"d"表示文件夹，"-"表示文件。例如：
```shell
# ls -la
total 2
dr-xr-x---, #省略后面部分
-rw-------, #省略后面部分
```

### 文件文本编辑命令

1. cat命令 
cat命令用于查看纯文本文件（内容较少的），格式为“cat [选项] [文件]”。加一个-n参数显示行号

```shell
# cat -n [文件]
# cat -n initial-setup-ks.cfg 
```

2. more命令 
more命令用于查看纯文本文件（内容较多的），格式为“more [选项] [文件]”。 

```shell
# more initial-setup-ks.cfg 
```

3. head命令
head命令用于查看纯文本文档的前N行，格式为“head [选项] [文件]”。

```shell
# head -n 20 initial-setup-ks.cfg 
```

4. tail命令 
tail命令用于查看纯文本文档的后N行或持续刷新内容，格式为“tail [选项] [文件]”。 
tail命令的操作方法与head命令非常相 似，只需要执行“tail -n 20 文件名”命令就可以达到这样的效果。tail命令 最强悍的功能是可以持续刷新一个文件的内容，当想要实时查看最新日志 文件时，这特别有用，此时的命令格式为“tail -f 文件名”

```shell
# tail -f /var/log/messages 
```


5. tr命令 
tr命令用于替换文本文件中的字符，格式为“tr [原始字符] [目标字符]”。
例如，把某个文本内容中的英文全部替 换为大写：

```shell
# cat anaconda-ks.cfg | tr [a-z] [A-Z] 
```

6. wc命令 
wc命令用于统计指定文本的行数、字数、字节数，格式为“wc [参数] 文本”。

-l 只显示行数
-w 只显示单词数
-c 只显示字节数

7. stat命令 
stat命令用于查看文件的具体存储信息和时间等信息，格式为“stat 文件名称”。 

8. cut命令 
cut命令用于按“列”提取文本字符，格式为“cut [参数] 文本”。 

9. diﬀ命令 
diﬀ命令用于比较多个文本文件的差异，格式为“diﬀ [参数] 文件”。
使用--brief参数来确认两个文件是否不同，
使用-c参数来详细比较出多个文件的差异之处

### 文件目录管理命令

1. touch命令 
touch命令用于创建空白文件或设置文件的时间，格式为“touch [选项] [文件]”。

2. mkdir命令 
mkdir命令用于创建空白的目录，格式为“mkdir [选项] 目录”。 
在Linux系统中，文件夹是最常见的文件类型之一。除了能创建单个空白目录外，mkdir命令还可以结合-p参数来递归创建出具有嵌套叠层关系的文件目录。

```shell
[root@linuxprobe ~]# mkdir linuxprobe 
[root@linuxprobe ~]# cd linuxprobe 
[root@linuxprobe linuxprobe]# mkdir -p a/b/c/d/e 
[root@linuxprobe linuxprobe]# cd a 
[root@linuxprobe a]# cd b 
[root@linuxprobe b]#
```
3. cp命令 
cp命令用于复制文件或目录，格式为“cp [选项] 源文件 目标文件”。 
在Linux系统中，复制操作具体分 为3种情况：
* 如果目标文件是目录，则会把源文件复制到该目录中； 
* 如果目标文件也是普通文件，则会询问是否要覆盖它； 
* 如果目标文件不存在，则执行正常的复制操作。 

4．mv命令 
mv命令用于剪切文件或将文件重命名，格式为“mv [选项] 源文件 [目标路径|目标文件名]”。

剪切操作不同于复制操作，因为它会默认把源文件删除掉，只保留剪 切后的文件。如果在同一个目录中对一个文件进行剪切操作，其实也就是 对其进行重命名：

```shell
# mv x.log linux.log 
# ls 
install.log linux.log 
```

5. rm命令 
rm命令用于删除文件或目录，格式为“rm [选项] 文件”。 
在Linux系统中删除文件时，系统会默认向您询问是否要执行删除操作，如果不想总是看到这种反复的确认信息，可在rm命令后跟上-f参数来 强制删除。另外，想要删除一个目录，需要在rm命令后面一个-r参数才可以，否则删除不掉。我们来尝试删除前面创建的install.log和linux.log文件：

[root@linuxprobe ~]# rm install.log 
rm: remove regular empty file ‘install.log’? y 
[root@linuxprobe ~]# rm -f linux.log 
[root@linuxprobe ~]# ls 
[root@linuxprobe ~]# 

 6. dd命令 dd命令用于按照指定大小和个数的数据块来复制文件或转换文件，格 式为“dd [参数]”。

 7. ﬁle命令 
 ﬁle命令用于查看文件的类型，格式为“ﬁle 文件名”。 
 
 在Linux系统中，由于文本、目录、设备等所有这些一切都统称为文件，而我们又不能单凭后缀就知道具体的文件类型，这时就需要使用ﬁle命 令来查看文件类型了。

[root@linuxprobe ~]# file anaconda-ks.cfg  anaconda-ks.cfg: ASCII text [root@linuxprobe ~]# file /dev/sda /dev/sda: block special 
 

### 打包压缩与搜索命令

1. tar命令
 tar命令用于对文件进行打包压缩或解压，格式为“tar [选项] [文件]”。-c 创建压缩文件
 
-x 解开压缩文件
-t 查看压缩包内有哪些文件
-z 用Gzip压缩或解压
-j 用bzip2压缩或解压
-v 显示压缩或解压的过程
-f 目标文件名
-p 保留原始的权限与属性
-P 使用绝对路径来压缩
-C 指定解压到的目录
