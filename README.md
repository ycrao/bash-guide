<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/2059754/24601246/753a7f36-1858-11e7-9d6b-7a0e64fb27f7.png" alt="bash logo"/>
</p>

> Fork 自 [Idnan/bash-guide](https://github.com/Idnan/bash-guide)，由 [raoyc](https://raoyc.com) 翻译为简体中文版，仅供参考学习使用，不可商用。

## 目录
  1. [基本操作](#1-基本操作)  
    1.1. [文件操作](#11-文件操作)  
    1.2. [文本操作](#12-文本操作)  
    1.3. [文件夹操作](#13-文件夹操作)  
    1.4. [SSH、系统信息及网络操作](#14-ssh系统信息及网络操作)  
    1.5. [进程监控操作](#15-进程监控操作)
  2. [基础Shell编程](#2-基础-shell-编程)  
    2.1. [变量](#21-变量)  
    2.2. [数组](#22-数组)  
    2.3. [字符串替换](#22-字符串替换)  
    2.4. [函数](#23-函数)  
    2.5. [条件语句](#24-条件语句)  
    2.6. [循环](#25-循环)  
  3. [技巧](#3-技巧)  
  4. [调试](#4-调试)  
  

# 1. 基本操作

### a. `export`
显示所有环境变量。如果你想获取某个特定（环境）变量详情值，请使用 `echo $VARIABLE_NAME` 。  
```bash
export
```
示例:
```bash
$ export
AWS_HOME=/Users/adnanadnan/.aws
LANG=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LESS=-R

$ echo $AWS_HOME
/Users/adnanadnan/.aws
```

### b. `whatis`
whatis 显示用户命令、系统调用、类库功能等在手册中描述。  
```bash
whatis something
```
示例:
```bash
$ whatis bash
bash (1)             - GNU Bourne-Again SHell
```

### c. `whereis`
whereis 通过系统自动建立的索引库来检索可执行程序、源代码文件以及手册页面。  
```bash
whereis name
```
示例:
```bash
$ whereis php
/usr/bin/php
```

### d. `which`
which 检索环境变量 `PATH` 所限定目录下的可执行文件。此命令会打印可执行文件完整路径。  
```bash
which program_name 
```
示例:
```bash
$ which php
/c/xampp/php/php
```

### e. clear
清除终端窗体所有内容。

## 1.1. 文件操作
<table>
   <tr>
      <td><a href="#a-cat">cat</a></td>
      <td><a href="#b-chmod">chmod</a></td>
      <td><a href="#c-chown">chown</a></td>
      <td><a href="#d-cp">cp</a></td>
      <td><a href="#e-diff">diff</a></td>
      <td><a href="#f-file">file</a></td>
      <td><a href="#g-find">find</a></td>
      <td><a href="#h-gunzip">gunzip</a></td>
      <td><a href="#i-gzcat">gzcat</a></td>
      <td><a href="#j-gzip">gzip</a></td>
      <td><a href="#k-head">head</a></td>
   </tr>
   <tr>
      <td><a href="#l-lpq">lpq</a></td>
      <td><a href="#m-lpr">lpr</a></td>
      <td><a href="#n-lprm">lprm</a></td>
      <td><a href="#o-ls">ls</a></td>
      <td><a href="#p-more">more</a></td>
      <td><a href="#q-mv">mv</a></td>
      <td><a href="#r-rm">rm</a></td>
      <td><a href="#s-tail">tail</a></td>
      <td><a href="#t-touch">touch</a></td>
   </tr>
</table>

### a. `cat`
在 UNIX 或 Linux 下，它可以用于以下场景：  
* 在屏幕上显示文本文件
* 复制文本文件
* 合并文本文件
* 创建新的文本文件
```bash
cat filename
cat file1 file2 
cat file1 file2 > newcombinedfile
```

### b. `chmod`
chmod 是 "change mode" (改变模式）的意思，它允许你改变文件读、写和可执行等权限。 关于此命令的详细信息请参考此[链接](https://ss64.com/bash/chmod.html)。
```bash
chmod -options filename
```

### c. `chown`
chown 是 "change owner" （更改所有者）的意思, 它允许你改变一个文件或文件夹的所有者，所有者可以是个用户或用户组。常见的用法是使用冒号来分隔，前面是用户，后面接着用户组。
```bash
chown -options user:group filename
```

### d. `cp`
把文件从一个位置复制到另一个位置。  
```bash
cp filename1 filename2
```
这里的 `filename1` 是原始文件路径，`filename2` 是目标文件路径。

### e. `diff`
比较文件并列出他们的不同。  
```bash
diff filename1 filename2
```

### f. `file`
侦测文件类型。  
```bash
file filename
```
示例:
```bash
$ file index.html
 index.html: HTML document, ASCII text
```
### g. `find`
在特定目录下查找文件。  
```bash
find directory options pattern
```
示例:
```bash
$ find . -name README.md
$ find /home/user1 -name '*.png'
```

### h. `gunzip`
解压缩由 gzip 压缩过的文件。  
```bash
gunzip filename
```

### i. `gzcat`
可让你免解压直接查看经 `gzip` 压缩过的文件。  
```bash
gzcat filename
```

### j. `gzip`
压缩文件。  
```bash
gzip filename
```

### k. `head`
输出文件前10行内容。  
```bash
head filename
```

### l. `lpq`
查看打印队列状态。  
```bash
lpq
```
示例:
```bash
$ lpq
Rank    Owner   Job     File(s)                         Total Size
active  adnanad 59      demo                            399360 bytes
1st     adnanad 60      (stdin)                         0 bytes
```

### m. `lpr`
打印文件。  
```bash
lpr filename
```

### n. `lprm`
从打印队列中移除某个任务。  
```bash
lprm jobnumber
```

### o. `ls`
列出文件。 `ls` 拥有诸多选项： `-l` 以列表方式列出文件 （包含文件大小，文件所属用户组，文件权限及其最后更新时间等）； `-a` 列出所有文件，包括隐藏文件。关于这个命令的更多信息请查阅此 [外链](https://ss64.com/bash/ls.html) 。  
```bash
ls option
```
示例:
<pre>
$ ls -la
rwxr-xr-x   33 adnan  staff    1122 Mar 27 18:44 .
drwxrwxrwx  60 adnan  staff    2040 Mar 21 15:06 ..
-rw-r--r--@  1 adnan  staff   14340 Mar 23 15:05 .DS_Store
-rw-r--r--   1 adnan  staff     157 Mar 25 18:08 .bumpversion.cfg
-rw-r--r--   1 adnan  staff    6515 Mar 25 18:08 .config.ini
-rw-r--r--   1 adnan  staff    5805 Mar 27 18:44 .config.override.ini
drwxr-xr-x  17 adnan  staff     578 Mar 27 23:36 .git
-rwxr-xr-x   1 adnan  staff    2702 Mar 25 18:08 .gitignore
</pre>

### p. `more`
展示文件的开头部分（通过敲击空格键移动以及 `q` 键退出）。  
```bash
more filename
```

### q. `mv`
将文件从一个位置移动到另一个位置。  
```bash
mv filename1 filename2
```
这里的 `filename1` 是原始文件路径，`filename2` 是目标文件路径。

此外它也可用于重命名一个文件。  
```bash
mv old_name new_name
```

### r. `rm`
移除某个文件。对一个目录使用此命令会爆出一个错误。  
`rm: directory: is a directory`
要删除一个目录，请传入 `-r` 参数，它将递归性删除该目录下所有内容。可选地你也使用 `-f` 标志位强制删除，也就是不经过任何确定提示等。  
```bash
rm filename
```

### s. `tail`
输出文件末尾10行内容。使用 `-f` 选项可输出正在被写入文件中的数据。  
```bash
tail filename
```

### t. `touch`
创建或更新你的文件。  
```bash
touch filename
```
示例:
```bash
$ touch trick.md
```

## 1.2. 文本操作

<table>
    <tr>
      <td><a href="#a-awk">awk</a></td>
      <td><a href="#b-cut">cut</a></td>
      <td><a href="#c-echo">echo</a></td>
      <td><a href="#d-egrep">egrep</a></td>
      <td><a href="#e-fgrep">fgrep</a></td>
      <td><a href="#f-fmt">fmt</a></td>
      <td><a href="#g-grep">grep</a></td>
      <td><a href="#h-nl">nl</a></td>
      <td><a href="#i-sed">sed</a></td>
      <td><a href="#j-sort">sort</a></td>
   </tr>
   <tr>
      <td><a href="#k-tr">tr</a></td>
      <td><a href="#l-uniq">uniq</a></td>
      <td><a href="#m-wc">wc</a></td>
   </tr>
</table>

### a. `awk`
awk 最佳的文本文件处理工具。它可以逐行处理整个文件。默认情况下，它使用空白符去切分为片段。awk 最常用的句法命令是：

```bash
awk '/search_pattern/ { action_to_take_if_pattern_matches; }' file_to_parse
```

让我们来看看下面 `/etc/passwd` 文件。这里是此文件中包含的样本数据：  
```
root:x:0:0:root:/root:/usr/bin/zsh
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
```
那么现在让我们从这个文件获取用户名。这里的 `-F` 指定我们想要字符串切分的分隔符，在本例中是 `:` 。 `{ print $1 }` 表示打印出第一个匹配到的字符片段。
```bash
awk -F':' '{ print $1 }' /etc/passwd
```
执行完上述命令后，你将得到下面输出：
```
root
daemon
bin
sys
sync
```
关于 `awk` 使用的更多信息请查阅此 [外链](https://www.cyberciti.biz/faq/bash-scripting-using-awk) 。


### b. `cut`
移除文件每行某些节内容。

*example.txt*
```bash
red riding hood went to the park to play
```

*以空格符为分隔符，显示第2、7和9节*
```bash
cut -d " " -f2,7,9 example.txt
```
```bash
riding park play
```

### c. `echo`
输出一行文字。

*显示 "Hello World"*
```bash
echo Hello World
```
```bash
Hello World
```

*单词间以新行方式显示 "Hello World"*
```bash
echo -ne "Hello\nWorld\n"
```
```bash
Hello
World
```

### d. `egrep`
打印出文件中匹配模式的行 - 扩展表达式  (视为 'grep -E' 的别名)

> 译者注：`egrep` 可以使用基本的正则表达外, 还可以用扩展表达式。

*example.txt*
```bash
Lorem ipsum
dolor sit amet, 
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*显示文件中包含 'Lorem' 或 'dolor' 的行*
```bash
egrep '(Lorem|dolor)' example.txt
or
grep -E '(Lorem|dolor)' example.txt
```
```bash
Lorem ipsum
dolor sit amet,
et dolore magna
duo dolores et ea
sanctus est Lorem
ipsum dolor sit
```

### e. `fgrep`
打印出文件中匹配模式的行 - 固化模式匹配  (视为 'grep -F' 的别名)

>   译者注：`fgrep` 指定的模式将不被认做正则表达式，而是确切的没有转义含义的字符串。

*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
foo (Lorem|dolor) 
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*在 example.txt 文件中找到确切的 '(Lorem|dolor)' 字符串*
```bash
fgrep '(Lorem|dolor)' example.txt
or
grep -F '(Lorem|dolor)' example.txt
```
```bash
foo (Lorem|dolor) 
```

### f. `fmt`
简单的文本格式化器。

*example: example.txt (1 行)*
```bash
Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.
```

*将 example.txt 格式化输出为20字符行宽*
```bash
cat example.txt | fmt -w 20
```
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

### g. `grep`
在文件中查找文本。你可以使用 grep 命令去查找匹配一个或多个正则表达式的文本行，然后输出匹配的结果行。 
```bash
grep pattern filename
```
示例：
```bash
$ grep admin /etc/passwd
_kadmin_admin:*:218:-2:Kerberos Admin Service:/var/empty:/usr/bin/false
_kadmin_changepw:*:219:-2:Kerberos Change Password Service:/var/empty:/usr/bin/false
_krb_kadmin:*:231:-2:Open Directory Kerberos Admin Service:/var/empty:/usr/bin/false
```
你也可以通过 `-i` 选项参数强制 grep 忽略大小写；`-r` 可被用来递归地查找指定目录下所有的文件。例如： 
```bash
$ grep -r admin /etc/
```
参数 `-w` 限定只查找单词。关于 `grep` 命令的更多帮助信息，请查阅此[外链](https://www.cyberciti.biz/faq/grep-in-bash)。

### h. `nl`
（显示）文件行号。

*example.txt*
```bash
Lorem ipsum
dolor sit amet,
consetetur
sadipscing elitr,
sed diam nonumy
eirmod tempor
invidunt ut labore
et dolore magna
aliquyam erat, sed
diam voluptua. At
vero eos et
accusam et justo
duo dolores et ea
rebum. Stet clita
kasd gubergren,
no sea takimata
sanctus est Lorem
ipsum dolor sit
amet.
```

*带行号显示 example.txt*
```bash
nl -s". " example.txt 
```
```bash
     1. Lorem ipsum
     2. dolor sit amet,
     3. consetetur
     4. sadipscing elitr,
     5. sed diam nonumy
     6. eirmod tempor
     7. invidunt ut labore
     8. et dolore magna
     9. aliquyam erat, sed
    10. diam voluptua. At
    11. vero eos et
    12. accusam et justo
    13. duo dolores et ea
    14. rebum. Stet clita
    15. kasd gubergren,
    16. no sea takimata
    17. sanctus est Lorem
    18. ipsum dolor sit
    19. amet.
```

### i. `sed`
流式编辑器用于过滤与转换文本。

*example.txt*
```bash
Hello This is a Test 1 2 3 4
```

*替换所有空格为连字符*
```bash
sed 's/ /-/g' example.txt
```
```bash
Hello-This-is-a-Test-1-2-3-4
```

*替换所有数字为字符 "d"*
```bash
sed 's/[0-9]/d/g' example.txt
```
```bash
Hello This is a Test d d d d
```

### j. `sort`
对文件行进行排序。

*example.txt*
```bash
f
b
c
g
a
e
d
```

*对 example.txt （译者注：按字母序）排序 *
```bash
sort example.txt
```
```bash
a
b
c
d
e
f
g
```

*对 example.txt 随机排序 *
```bash
sort example.txt | sort -R
```
```bash
b
f
a
c
d
g
e
```

### k. `tr`
转换或删除字符

*example.txt*
```bash
Hello World Foo Bar Baz!
```

*把所有小写字母转换成大写形式*
```bash
cat example.txt | tr 'a-z' 'A-Z' 
```
```bash
HELLO WORLD FOO BAR BAZ!
```

*把所有空格转换为新行*
```bash
cat example.txt | tr ' ' '\n'
```
```bash
Hello
World
Foo
Bar
Baz!
```

### l. `uniq`
汇报或删除重复的行

*example.txt*
```bash
a
a
b
a
b
c
d
c
```

*显示 example.txt 中所有不重复的行 (首先你需要排序，否则部分相同行会被忽略)*
```bash
sort example.txt | uniq
```
```bash
a
b
c
d
```

*显示去重后的所有唯一项，并标注原始文件中该项出现的次数*
```bash
sort example.txt | uniq -c
```
```bash
    3 a
    2 b
    2 c
    1 d
```

### m. `wc`
告知你该文件的行数、词数（译者注：原文此处为 `words` ，对应英文来说，单词间一般以空白符或标点符分隔，一个单词算一个，但对于中文，一个不带空白符与标点符的长句仍算一个）与字节数（译者注：原文此处为 `characters` 应理解为字节数而非字符数）。 
```bash
wc filename
```
示例：
```bash
$ wc demo.txt
7459   15915  398400 demo.txt
```
这里，`7459` 是行数， `15915` 是词数以及 `398400` 是字节数。

## 1.3. 文件夹操作

<table>
   <tr>
      <td><a href="#a-cd">cd</a></td>
      <td><a href="#b-mkdir">mkdir</a></td>
      <td><a href="#c-pwd">pwd</a></td>
   </tr>
</table>

### a. `cd`
从一个目录跳转到另一个目录。执行下面命令会让你跳转到用户主目录。
```bash
$ cd
```
此命令接受一个可选的 `dirname` 参数，指向你想进入到的目录。
```bash
cd dirname
```

### b. `mkdir`
创建一个新的文件夹。  
```bash
mkdir dirname
```

### c. `pwd`
显示你当前所在目录的路径。
```bash
pwd
```

## 1.4. SSH、系统信息及网络操作

<table>
   <tr>
      <td><a href="#a-bg">bg</a></td>
      <td><a href="#b-cal">cal</a></td>
      <td><a href="#c-date">date</a></td>
      <td><a href="#d-df">df</a></td>
      <td><a href="#e-dig">dig</a></td>
      <td><a href="#f-du">du</a></td>
      <td><a href="#g-fg">fg</a></td>
      <td><a href="#h-finger">finger</a></td>   
      <td><a href="#i-jobs">jobs</a></td>
      <td><a href="#j-last">last</a></td>
   </tr>
   <tr>
      <td><a href="#k-man">man</a></td>
      <td><a href="#l-passwd">passwd</a></td>
      <td><a href="#m-ping">ping</a></td>
      <td><a href="#n-ps">ps</a></td>
      <td><a href="#o-quota">quota</a></td>
      <td><a href="#p-scp">scp</a></td>
      <td><a href="#q-ssh">ssh</a></td>
      <td><a href="#r-top">top</a></td>
      <td><a href="#s-uname">uname</a></td>
      <td><a href="#t-uptime">uptime</a></td>
   </tr>
   <tr>
      <td><a href="#u-w">w</a></td>
      <td><a href="#v-wget">wget</a></td>
      <td><a href="#w-whoami">whoami</a></td>
      <td><a href="#x-whois">whois</a></td>
   </tr>
</table>

### a. `bg`
列出所有被停止或后台运行的任务，或恢复一个已停止的任务到后台运行。

### b. `cal`
显示当前月月历。

### c. `date`
显示当前日期与实际。

### d. `df`
显示磁盘使用情况。

### e. `dig`
获取域名 DNS 解析相关信息。
```bash
dig domain
```

### f. `du`
显示文件或目录的磁盘使用情况。关于此命令的更新信息，请查阅此[外链](http://www.linfo.org/du.html)。
```bash
du [option] [filename|directory]
```
选项:
- `-h` (人类可读的) 把结果以 K、M、G（译者注：`K/M/G` 为磁盘占用空间大小的单位，`1G = 1024M` , `1M = 1024K` , `1K = 1024B` ，`1B = 8bit` ，其中 `B` 表示字节，`bit` 表示位）为单位输出。
- `-s` (压缩或总结) 输出该目录总的磁盘空间及其子目录总结性的报告。

示例:
```bash
du -sh pictures
1.4M pictures
```

### g. `fg`
将前台最近运行的任务列出来。

### h. `finger`
显示用户相关信息。  
```bash
finger username
```

### i. jobs
列出后台正在运行的任务，并给出任务号。

### j. `last`
列出指定用户最近登录记录。
```bash
last yourUsername
```

### k. `man`
显示特定命令帮助手册。
```bash
man command
```

### l. `passwd`
让当前登录的用户修改他的密码。

### m. `ping`
ping 某个主机并输出结果。  
```bash
ping host
```

### n. `ps`
列出用户进程。
```bash
ps -u yourusername
```

### o. `quota`
显示你的磁盘配额情况。  
```bash
quota -v
```

### p. `scp`
在本地主机与远程主机之间或两个远程主机之间传输文件。

*从本地主机复制文件到远程主机*
```bash
scp source_file user@host:directory/target_file
```
*从远程主机复制文件到本地主机*
```bash
scp user@host:directory/source_file target_file
scp -r user@host:directory/source_folder farget_folder
```
此命令也可接受 `-P` 选项，用来连接到特定的端口。
```bash
scp -P port user@host:directory/source_file target_file
```

### q. `ssh`
ssh （ssh 客户端）是一个用来登录到远程机器并在远程机器上执行命令的程序。
```bash
ssh user@host
```
此命令也可接受 `-P` 选项参数，用来连接到特定的端口。
```bash
ssh -p port user@host
```

### r. `top`
显示你当前活跃的进程。

### s. `uname`
显示内核信息。
```bash
uname -a
```

### t. `uptime`
显示当前运行时间（译者注：即从机器上一次开机算起，到现在的在线待机时间）。

### u. `w`
显示当前在线用户。

### v. `wget`
下载文件。
```bash
wget file
```

### w. `whoami`
返回当前登录用户的名字。

### x. `whois`
获取某个域名的 whois 信息。  
```bash
whois domain
```

## 1.5. 进程监控操作

<table>
   <tr>
      <td><a href="#a-kill">kill</a></td>
      <td><a href="#b-killall">killall</a></td>
      <td><a href="#c-&">&amp;</a></td>
      <td><a href="#d-nohup">nohup</a></td>
   </tr>
</table>

### a. `kill`
根据给定的进程 ID 杀死（结束）该进程 
```bash
kill PID
```

### b. `killall`
杀死以此为名字的所有进程。 
```bash
killall processname
```

### c. &
`&` 标志可以使命令作为后台进程运行在 subshell 中。
```bash
command &
```

### d. `nohup`
nohup 代表 `No Hang Up` （不要挂起）的含义。它允许其它命令、进程或 shell 脚本在你终端登出之后继续在后台运行。
```bash
nohup command
```
把它和 `&` 结合可以创建后台进程。
```bash
nohup command &
```

# 2. 基础 Shell 编程


The first line that you will write in bash script files is called `shebang`. This line in any script determines the script's ability to be executed like a standalone executable without typing sh, bash, python, php etc beforehand in the terminal.

```bash
#!/bin/bash
```

## 2.1. 变量

Creating variables in bash is similar to other languages. There are no data types. A variable in bash can contain a number, a character, a string of characters, etc. You have no need to declare a variable, just assigning a value to its reference will create it.

Example:
```bash
str="hello world"
```

The above line creates a variable `str` and assigns "hello world" to it. The value of variable is retrieved by putting the `$` in the beginning of variable name.

Example:
```bash
echo $str   # hello world
```

Like other languages bash has also arrays. An array is variable containing multiple values. There's no maximum limit on the size of array. Array in bash are zero based. The first element is indexed with element 0. There are several ways for creating arrays in bash. Which are given below.

Examples:
```bash
array[0] = val
array[1] = val
array[2] = val
array=([2]=val [0]=val [1]=val)
array=(val val val)
```
To display a value at specific index use following syntax:

```bash
${array[i]}     # where i is the index
```

If no index is supplied, array element 0 is assumed. To find out how many values there are in the array use the following syntax:

```bash
${#array[@]}
```

Bash has also support for the ternary conditions. Check some examples below.

```bash
${varname:-word}    # if varname exists and isn't null, return its value; otherwise return word
${varname:=word}    # if varname exists and isn't null, return its value; otherwise set it word and then return its value
${varname:+word}    # if varname exists and isn't null, return word; otherwise return null
${varname:offset:length}    # performs substring expansion. It returns the substring of $varname starting at offset and up to length characters
```

## 2.2 字符串替换

Check some of the syntax on how to manipulate strings

```bash
${variable#pattern}         # if the pattern matches the beginning of the variable's value, delete the shortest part that matches and return the rest
${variable##pattern}        # if the pattern matches the beginning of the variable's value, delete the longest part that matches and return the rest
${variable%pattern}         # if the pattern matches the end of the variable's value, delete the shortest part that matches and return the rest
${variable%%pattern}        # if the pattern matches the end of the variable's value, delete the longest part that matches and return the rest
${variable/pattern/string}  # the longest match to pattern in variable is replaced by string. Only the first match is replaced
${variable//pattern/string} # the longest match to pattern in variable is replaced by string. All matches are replaced
${#varname}     # returns the length of the value of the variable as a character string
```

## 2.3. 函数
As in almost any programming language, you can use functions to group pieces of code in a more logical way or practice the divine art of recursion. Declaring a function is just a matter of writing function my_func { my_code }. Calling a function is just like calling another program, you just write its name.

```bash
functname() {
    shell commands
}
```

Example:
```bash
#!/bin/bash
function hello {
   echo world!
}
hello

function say {
    echo $1
}
say "hello world!"
```

When you run the above example the `hello` function will output "world!". The above two functions `hello` and `say` are identical. The main difference is function `say`. This function, prints the first argument it receives. Arguments, within functions, are treated in the same manner as arguments given to the script.

## 2.4. 条件

The conditional statement in bash is similar to other programming languages. Conditions have many form like the most basic form is `if` expression `then` statement where statement is only executed if expression is true.

```bash
if [expression]; then
    will execute only if expression is true
else
    will execute if expression is false
fi
```

Sometime if conditions becoming confusing so you can write the same condition using the `case statements`.

```bash
case expression in
    pattern1 )
        statements ;;
    pattern2 )
        statements ;;
    ...
esac
```

Expression Examples:

```bash
statement1 && statement2  # both statements are true
statement1 || statement2  # one of the statement is true

str1=str2       # str1 matches str2
str1!=str2      # str1 does not match str2
str1<str2       # str1 is less than str2
str1>str2       # str1 is greater than str2
-n str1         # str1 is not null (has length greater than 0)
-z str1         # str1 is null (has length 0)

-a file         # file exists
-d file         # file exists and is a directory
-e file         # file exists; same -a
-f file         # file exists and is a regular file (i.e., not a directory or other special type of file)
-r file         # you have read permission
-s file         # file exists and is not empty
-w file         # your have write permission
-x file         # you have execute permission on file, or directory search permission if it is a directory
-N file         # file was modified since it was last read
-O file         # you own file
-G file         # file's group ID matches yours (or one of yours, if you are in multiple groups)

file1 -nt file2     # file1 is newer than file2
file1 -ot file2     # file1 is older than file2

-lt     # less than
-le     # less than or equal
-eq     # equal
-ge     # greater than or equal
-gt     # greater than
-ne     # not equal
```

## 2.5. 循环

There are three types of loops in bash. `for`, `while` and `until`.

Different `for` Syntax:
```bash
for x := 1 to 10 do
begin
  statements
end

for name [in list]
do
  statements that can use $name
done

for (( initialisation ; ending condition ; update ))
do
  statements...
done
```

`while` Syntax:
```bash
while condition; do
  statements
done
```

`until` Syntax:
```bash
until condition; do
  statements
done
```

# 3. 技巧

## 设置别名
使用下面命令 `nano ~/.bash_profile` （译者注：当然你也可使用 `vi/vim` 工具，前提你已经安装过该软件包）打开 `bash_profile`  
> alias dockerlogin='ssh www-data@adnan.local -p2222'  # add your alias in .bash_profile

## 快速跳转到指定目录
nano ~/.bashrc
> export hotellogs="/workspace/hotel-api/storage/logs"

```bash
source ~/.bashrc
cd $hotellogs
```

## 跳出陷阱

通过可靠地执行清理代码使得你的脚本更加健壮。

```bash
function finish {
  # 你的清理代码，如 杀死所有 forked 进程
  jobs -p | xargs kill
}
trap finish EXIT
```

## 保存你的环境变量

当你执行 `export FOO = BAR` 时，你的环境变量只在当前及其子 shell 中存在，想在将来持久化它，只需追加以下命令导出你的变量到 `~/.bash_profile` 文件。
```bash
echo export FOO=BAR >> ~/.bash_profile
```

## 访问你的脚本

通过在你的用户主目录创建一个 bin 目录，即使用 `mkdir ~/bin` 命令，在此 bin 目录下的所有脚本都能在任何别的目录中快速访问到。 

如果你无法访问，尝试追加以下代码到 `~/.bash_profile` 文件，随后执行 `source ~/.bash_profile` 命令。
```bash
    # 设置 PATH 如果用户私有 bin 目录存在，则包括进去
    if [ -d "$HOME/bin" ] ; then
        PATH="$HOME/bin:$PATH"
    fi
```

# 4. 调试
通过传入不同的 bash 选项参数，你可很方便地调试脚本代码。例如：`-n` 将只检查语法而不执行命令；`-v` 会在执行之前输出命令；`-x` 将在命令处理后输出命令。

```bash
bash -n scriptname
bash -v scriptname
bash -x scriptname
```

## 贡献

- 报告问题 [官方帮助](https://help.github.com/articles/creating-an-issue/)
- 提交改进后的 pull request [官方帮助](https://help.github.com/articles/about-pull-requests/)
- 宣传本文档

## 翻译版本

> 译者注：官方已列出早期他人贡献的中文翻译版本，译者本人的翻译[链接](https://github.com/ycrao/bash-guide)，只为加深理解，在翻译中，修正了部分表述错误的地方（有译注说明），他我二人（ `vuuihc` 与 我 `ycrao` ）在翻译表述也并不尽相同，请读者自行辨别取舍阅读。

- [Chinese | 简体中文](https://github.com/vuuihc/bash-guide)
- [Turkish | Türkçe](https://github.com/omergulen/bash-guide)
- [Japanese | 日本語](https://github.com/itooww/bash-guide)

## 授权协议

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
