
## GNU Build system
```bash
configure.ac: AM_GNU_GETTEXT_VERSION is used, but not AM_GNU_GETTEXT
configure.ac:79: error: possibly undefined macro: AM_GNU_GETTEXT
```
GNU build system 不全面, 重装automake-1.14
```bash
#安装m4
wget  [http://mirrors.kernel.org/gnu/m4/m4-1.4.13.tar.gz](http://mirrors.kernel.org/gnu/m4/m4-1.4.13.tar.gz)  \  
&& tar -xzvf m4-1.4.13.tar.gz \  
&& cd m4-1.4.13 \  
&& ./configure –prefix=/usr/local  
make && make install
#安装autoconf
wget  [http://mirrors.kernel.org/gnu/autoconf/autoconf-2.65.tar.gz](http://mirrors.kernel.org/gnu/autoconf/autoconf-2.65.tar.gz)  \  
&& tar -xzvf autoconf-2.65.tar.gz \  
&& cd autoconf-2.65 \  
&& ./configure –prefix=/usr/local  
make && make install
#安装automake
wget  [http://mirrors.kernel.org/gnu/automake/automake-1.11.tar.gz](http://mirrors.kernel.org/gnu/automake/automake-1.11.tar.gz)  \  
&& tar xzvf automake-1.11.tar.gz \  
&& cd automake-1.11 \  
&& ./configure –prefix=/usr/local  
make && make install
#安装libtool
wget  [http://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz](http://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz)  \  
&& tar xzvf libtool-2.2.6b.tar.gz \  
&& cd libtool-2.2.6b \  
&& ./configure –prefix=/usr/local  
make && make install
```
## umask
```bash
下面是另外一个例子，假设这次u m a s k值为0 2 2：
　　1) 文件的最大权限 rwx rwx rwx (777)
　　2 ) u m a s k值为0 2 2 --- -w- -w-
　　3) 目录权限 rwx r-x r-x (755) 这就是目录创建缺省权限
　　4) 文件权限 rw- r-- r-- (644) 这就是文件创建缺省权限
```
## bashrc

在 /etc目录的bashrc和profile是系统级（全局）的配置文件，当在用户主目录下找不到.bash_profile 和.bashrc时，就会读取这两个文件。.bash_history是bash shell的历史记录文件，里面记录了你在bash shell中输入的所有命令。可通过HISSIZE环境变量设置在历史记录文件里保存记录的条数。alias l = 'ls -l'是设置别名的语句，把它放在这些配置文档中就可使我们能用简单的'l'命令，代替'ls -l'命令。

登录Shell(不管是不是交互式的)文件加载顺序如下:  

```bash
/etc/profile
~/.bash_profile
~/.bash_login
~/.profile
```

交互式非登录Shell文件加载顺序如下：

```bash
/etc/bashrc
~/.bashrc
```
```bash
1. bashrc是在系统启动后就会自动运行。
2. profile是在用户登录后才会运行。
3. 进行设置后，可运用source bashrc命令更新bashrc，也可运用source profile命令更新profile。
4. ~/.bash_profile: 每个用户都可使用该文件输入专用于自己使用的shell信息，当用户登录时，该文件仅仅执行一次!默认情况下,他设置一些环境变量,执行用户的.bashrc文件。
5. ~/.bash_logout: 当每次退出系统(退出bash shell)时，执行该文件。
6. ~/.bash_profile 是交互式、login方式进入bash运行的，~/.bashrc是交互式non-login方式进入bash运行的，通常二者设置大致相同，所以通常前者会调用后者。
```
## SCP
```bash
1、scp指定端口传输，端口需放在scp后面

scp -P 34543 -r spark xiaojp@120.26.233.3:~/

2、ssh指定端口登录：

ssh -p 34543 xiaojp@120.26.233.3
密钥权限要为400
E:\Workspace\ITools\Tencent>scp -i chengdu 1016.png root@129.28.65.64:/root
上传文件利用cygwin里的scp可用
scp -i <keyfile> <fileToUpload> <username>@ip:<path>
下载
scp -i chengdu root@129.28.65.64:/root/prometheus-2.3.2.linux-amd64.tar.gz .
补充: https://blog.csdn.net/qq_27528801/article/details/51539869
-r 可以用于复制文件夹

```
## Crontab
```bash
-e：编辑该用户的计时器设置；
-l：列出该用户的计时器设置；
-r：删除该用户的计时器设置；
-u<用户名称>：指定要设定计时器的用户名称。
```
`/etc/crontab`文件包括下面几行：
```bash
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=""
HOME=/

# run-parts
51 * * * * root run-parts /etc/cron.hourly
24 7 * * * root run-parts /etc/cron.daily
22 4 * * 0 root run-parts /etc/cron.weekly
42 4 1 * * root run-parts /etc/cron.monthly
```
前四行是用来配置crond任务运行的环境变量，第一行SHELL变量指定了系统要使用哪个shell，这里是bash，第二行PATH变量指定了系统执行命令的路径，第三行MAILTO变量指定了crond的任务执行信息将通过电子邮件发送给root用户，如果MAILTO变量的值为空，则表示不发送任务执行信息给用户，第四行的HOME变量指定了在执行命令或者脚本时使用的主目录。

**用户任务调度**：用户定期要执行的工作，比如用户数据备份、定时邮件提醒等。用户可以使用 crontab 工具来定制自己的计划任务。所有用户定义的crontab文件都被保存在`/var/spool/cron`目录中。其文件名与用户名一致，使用者权限文件如下：
```bash
/etc/cron.deny     该文件中所列用户不允许使用crontab命令
/etc/cron.allow    该文件中所列用户允许使用crontab命令
/var/spool/cron/   所有用户crontab文件存放的目录,以用户名命名
```
/usr/local/qcloud/stargate/admin/start.sh

```bash
```
```bash
```
```bash
```
```bash
```
```bash
```
```bash
```
## lighttpd
```bash
```
## rsync rsync_snapshot
站点更新, 备份
```bash
git clone git://git.samba.org/rsync.git
```
## Time Machine＆Nettalk
https://www.jianshu.com/p/8716022d6551
https://www.v2ex.com/t/99081
##  Snapper
## Mahavairocana 运维佛法
```bash
# 系统监控
https://www.cnblogs.com/Mahavairocana/p/8261686.html
```
一个小运维
https://home.cnblogs.com/u/george-guo/

> Written with [StackEdit](https://stackedit.io/).


## Katura
通过 `sudo -i` 变成管理员模式 root
https://blog.csdn.net/u012857400/article/details/78423970

## 荣锋亮
https://www.cnblogs.com/rongfengliang/category/793037.html

## 用户
adduser testuser //新建testuser 用户 passwd testuser  
addgroup
chgrp

## /bin /usr/bin /usr/sbin /sbin
在linux下我们经常用到的四个应用程序的目录是/bin、/sbin、/usr/bin、/usr/sbin 。而四者存放的文件一般如下：

**bin目录:**

bin为binary的简写主要放置一些[系统](http://www.2cto.com/os/)的必备执行档例如:cat、cp、chmod df、dmesg、gzip、kill、ls、mkdir、more、mount、rm、su、tar等。

**/usr/bin目录:**
主要放置一些应用软件工具的必备执行档例如c++、g++、gcc、chdrv、diff、dig、du、eject、elm、free、gnome*、 zip、htpasswd、kfm、ktop、last、less、locale、m4、make、man、mcopy、ncftp、 newaliases、nslookup passwd、quota、smb*、wget等。
**/sbin目录:**
主要放置一些系统管理的必备程序例如:cfdisk、dhcpcd、dump、e2fsck、fdisk、halt、ifconfig、ifup、 ifdown、init、insmod、lilo、lsmod、mke2fs、modprobe、quotacheck、reboot、rmmod、 runlevel、shutdown等。
**/usr/sbin目录:**
放置一些网路管理的必备程序例如:dhcpd、httpd、imap、in.*d、inetd、lpd、named、netconfig、nmbd、samba、sendmail、squid、swap、tcpd、tcpdump等
综述：
**如果这是用户和管理员必备的二进制文件，就会放在/bin。如果这是系统管理员必备，但是一般用户根本不会用到的二进制文件，就会放在 /sbin。**
**相对而言。如果不是用户必备的二进制文件，多半会放在/usr/bin；如果不是系统管理员必备的工具，多半会放在/usr/sbin。**

`/usr`：系统级的目录，可以理解为`C:/Windows/`，`/usr/lib`理解为`C:/Windows/System32`。  
`/usr/local`：用户级的程序目录，可以理解为`C:/Progrem Files/`。用户自己编译的软件默认会安装到这个目录下。  
`/opt`：用户级的程序目录，可以理解为`D:/Software`，opt有可选的意思，这里可以用于放置第三方大型软件（或游戏），当你不需要时，直接`rm -rf`掉即可。在硬盘容量不够时，也可将/opt单独挂载到其他磁盘上使用。

源码放哪里？  
`/usr/src`：系统级的源码目录。  
`/usr/local/src`：用户级的源码目录。

/opt
 Here’s where optional stuff is put. Trying out the latest Firefox beta? Install it to /opt where you can delete it without affecting other settings. Programs in here usually live inside a single folder whick contains all of their data, libraries, etc.这里主要存放那些可选的程序。你想尝试最新的firefox测试版吗?那就装到/opt目录下吧，这样，当你尝试完，想删掉firefox的时候，你就可 以直接删除它，而不影响系统其他任何设置。安装到/opt目录下的程序，它所有的数据、库文件等等都是放在同个目录下面。  
 举个例子：刚才装的测试版firefox，就可以装到/opt/firefox_beta目录下，/opt/firefox_beta目录下面就包含了运 行firefox所需要的所有文件、库、数据等等。要删除firefox的时候，你只需删除/opt/firefox_beta目录即可，非常简单。
/usr/local
 This is where most manually installed(ie. outside of your package manager) software goes. It has the same structure as /usr. It is a good idea to leave /usr to your package manager and put any custom scripts and things into /usr/local, since nothing important normally lives in /usr/local.
> 这里主要存放那些手动安装的软件，即不是通过“新立得”或apt-get安装的软件。它和/usr目录具有相类似的目录结构。让软件包管理器来管理/usr目录，而把自定义的脚本(scripts)放到/usr/local目录下面，我想这应该是个不错的主意。
## Adduser  Groupadd
```bash
adduser testuser //新建testuser 用户 
passwd testuser //给testuser 用户设置密码  
```
```bash
groupadd testgroup   //新建test工作组  
useradd -g testgroup testuser 	
//新建testuser用户并增加到testgroup工作组  
//注：：-g 所属组 -d 家目录 -s 所用的SHELL  
```

## Snapper
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/ch-snapper

## 一些库
M4 是一个宏处理器.将输入拷贝到输出,同时将宏展开. 宏可以是内嵌的也可以是用户定义的. 除了可以展开宏,m4还有一些内建的函数,用来引用文件,执行Unix命令,整数运算,文本操作,循环等. m4既可以作为编译器的前端也可以单独作为一个宏处理器.  
安装下列程序: m4  
简短说明  
m4 将输入拷贝到输出,同时将宏展开. 宏可以是内嵌的也可以是用户定义的. 除了可以展开宏,m4还有一些内建的函数,用来引用文件,执行Unix命令,整数运算,文本操作,循环等. m4既可以作为编译器的前端也可以单独作为一个宏处理器。  
M4 安装依赖关系  
M4 依赖于: Bash, Binutils, Coreutils, Diffutils, GCC, Gettext, Glibc, Grep, Make, Perl, Sed.

## 安装GNU开发工具
```bash
yum group install 'Development Tools' # CENTOS
dnf group install 'Development Tools  # FEDORA
sudo apt-get install build-essential 	# Debian/Ubuntu
```
## fswatch
```bash
fswatch [option] [path]
```
```bash
fswatch -M # 显示所有显示器
```
poll_monitor ; inotify_monitor/ windows_monitor
```bash
fswatch -x #print event flag
fswatch -t #print timestamp
fswatch -r #recursively
fswatch -i #recursively
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxNDg1ODI3NCwtMzI0NDc4NzU2LDIwMD
M0MTI4NTcsMTAzMTE0MTUyOF19
-->