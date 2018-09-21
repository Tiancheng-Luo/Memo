## 目标
建立一个全局变量temp, 表示为当前新建工作目录,
以它为坐标进行活动
解除temp
参考xargs mkdir

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

## 升级glib 先删除后装
https://blog.csdn.net/Aries1995/article/details/48968063
```bash
//32位版本  
#rm -rf /usr/bin/glib*  
#rm -rf /usr/include/glib-2.0  
#rm -rf /usr/lib/glib*  
  
//64位版本要多删下面两个  
#rm -rf /usr/lib64/glib*  
#rm -rf /usr/lib64/glib-2.0  
  
鼠标双击解压：glib-2.40.0.tar.xz  
//进入glib-2.40.0目录  
#cd glib-2.40.0  
  
//配置32位系统临时环境，自己根据系统选  
#export LD_LIBRARY_PATH=/usr/lib  
#export PKG_CONFIG_PATH=/usr/lib/pkgconfig  
  
//配置64位系统临时环境，自己根据系统选  
#export LD_LIBRARY_PATH=/usr/lib64  
#export PKG_CONFIG_PATH=/usr/lib64/pkgconfig  
  
//配置32位系统，自己根据系统选  
#./configure --prefix=/usr --libdir=/usr/lib  
  
//配置64位系统，自己根据系统选  
#./configure --prefix=/usr --libdir=/usr/lib64  
  
//编译  
#make  
//安装  
#make install
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


```bash
chgrp [-cfhRv][--help][--version][所属群组][文件或目录...]  或 chgrp [-cfhRv][--help][--reference=<参考文件或目录>][--version][文件或目录...]
chgrp -R mengxin /usr/meng
```
选项  
-c或——changes：效果类似“-v”参数，但仅回报更改的部分；
-f或--quiet或——silent：不显示错误信息；
-h或--no-dereference：只对符号连接的文件作修改，而不是该其他任何相关文件；
-R或——recursive：递归处理，将指令目录下的所有文件及子目录一并处理；
-v或——verbose：显示指令执行过程；
--reference=<参考文件或目录>：把指定文件或目录的所属群组全部设成和参考文件或目录的所属群组相同；
 参数  
 组：指定新工作名称；
-文件：指定要改变所属组的文件列表。多个文件或者目录之间使用空格隔开
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
# 显示全部 group
yum grouplist
yum group install 'Development Tools' # CENTOS
dnf group install 'Development Tools  # FEDORA
sudo apt-get install build-essential 	# Debian/Ubuntu

# Perhaps you have repositories configured which 
# conflict with this package group. See if this works:  
  
yum clean all  
yum groupinstall --disablerepo=\* --enablerepo=base,updates,cr "Development Tools"
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

## Coreutils
### stat
 stat -c --format
 stat -f --filesystem
 
 ### gpg gpg2
 gpg --verify coreutils-8.30.tar.xz.sig  coreutils-8.30.tar.xz
gpg: Signature made Mon 02 Jul 2018 09:41:43 AM CST using RSA key ID 306037D9
gpg: Can't check signature: No public key
 
gpg --recv-keys 306037D9   # --keyserver  keys.gnupg.net


gpg --verify --verbose coreutils-8.30.tar.xz.sig  coreutils-8.30.tar.xz
Version: GnuPG v2
gpg: armor header: 
gpg: Signature made Mon 02 Jul 2018 09:41:43 AM CST using RSA key ID 306037D9
gpg: using PGP trust model
gpg: Good signature from "P谩draig Brady <P@draigBrady.com>"
gpg:                 aka "P谩draig Brady <pixelbeat@gnu.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 6C37 DC12 121A 5006 BC1D  B804 DF6F D971 3060 37D9
gpg: binary signature, digest algorithm SHA256

## ls -l

![ls -l 意义](https://img-blog.csdn.net/20170820002015682?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemh1b3lhXw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)


## Gettext
yum install libtool gettext intltool

## openssh
sudo apt-get install openssh-server  
查询其服务时候安装成功的命令：  
netstat -tlp  
如显示如下结果，即表明服务启动成功：
1.  tcp 0 0 *:ssh *:* LISTEN
## 编译coreutils 失败
./configure 
./configure: line 4746: gl_EARLY: command not found
./configure: line 4747: gl_INIT: command not found
./configure: line 4748: coreutils_MACROS: command not found
./configure: line 4815: syntax error near unexpected token `-Werror,'
./configure: line 4815: `  gl_WARN_ADD(-Werror, WERROR_CFLAGS)'

automake
error: GL_GENERATE_ALLOCA_H does not appear in AM_CONDITIONAL
Makefile.am:211:   'lib/local.mk' included from here
lib/local.mk:1:   'lib/gnulib.mk' included from here
lib/gnulib.mk:271: error: GL_GENERATE_BYTESWAP_H does not appear in AM_CONDITIONAL
Makefile.am:211:   'lib/local.mk' included from here
lib/local.mk:1:   'lib/gnulib.mk' included from here
lib/gnulib.mk:711: error: GL_GENERATE_ERRNO_H does not appear in AM_CONDITIONAL


## virtualbox
```bash
# List virtual machines 
VBoxManage list vms 
# "MyVM"  {e4b0c92c-4301-4a7d-8af8-fe02fed00451}  
# Start VM in headless mode 
VBoxManage startvm MyVM --type headless 
# Power off VM 
VBoxManage controlvm MyVM poweroff
```

http://ju.outofmemory.cn/entry/84388

I. 控制芯片

几个不同的 driver 目测没有显著差别，只不过不同的 host/guest 对驱动的支持范围不同，哪个能用就选哪个。唯一例外是 virtio-net，由于它是半虚拟化的 driver（出自 KVM），性能可能会好一点。
 II. 连接模式
1.  NAT，guest 可访问 host 和外网，但外界不能访问 guest。除非设置端口转发。
    
2.  Bridged，guest 通过网卡桥接直连外网，与 host 之间相当于 LAN 里的两台独立机器。
    
3.  Internal，guest 与其他 guest 之间可互相通信，但 host 无法访问，也无法做端口转发。
    
4.  Host-Only，所有 guest 的通信都会经过 host 的一个虚拟网卡（host 相当于网关），所以 host 与 guest(s) 间可互相通信（但是 guest 对外网不可见）
    

相互对比一下会发现 NAT 和 Host-Only 实用价值较明显。如果 host 不需要访问 guest，用 NAT（或者只需要访问某个端口，映射比较方便）。如果需要较复杂的网络通信，用 Host-Only，然后给需要访问外网的 guest 加上 NAT。Host-Only 相对于 NAT 的优势在于更清晰的网络划分（有点类似 Linux 里 brctl + iptables 给 LXC 设立的网络环境）。

## III. 奇怪的 “Promiscuous Mode”

上面提到的文章以及 VirtualBox 的官方文档都没有讲清楚 Promiscuous Mode 究竟是什么东西，这里摘录  [Wikipedia 的解释](http://zh.wikipedia.org/wiki/Promiscuous_mode)：

> 一般计算机网卡都工作在非混杂模式下，此时网卡只接受来自网络端口的目的地址指向自己的数据。当网卡工作在混杂模式下时，网卡会捕获来自接口的所有数据并交给相应的驱动程序。网卡的混杂模式一般在网络管理员分析网络数据作为网络故障诊断手段时用到，同时这个模式也被网络黑客利用来作为网络数据窃听的入口。在Linux操作系统中设置网卡混杂模式时需要管理员权限。在Windows操作系统和Linux操作系统中都有使用混杂模式的抓包工具，比如著名的开源软件Wireshark。
## 现成的测试脚本
[phoronix-test-suite测试云服务器](https://www.cnblogs.com/tanyongli/p/7767804.html)
https://www.cnblogs.com/tanyongli/p/7767804.html
搜索 云服务器 测试脚本
https://www.baidu.com/s?ie=utf-8&f=8&rsv_bp=1&rsv_idx=2&tn=baiduhome_pg&wd=%E4%BA%91%E6%9C%8D%E5%8A%A1%E5%99%A8%20%E6%B5%8B%E8%AF%95%E8%84%9A%E6%9C%AC&rsv_spt=1&oq=%25E4%25BA%2591%25E6%259C%258D%25E5%258A%25A1%25E5%2599%25A8%2520%25E6%25B5%258B%25E8%25AF%2595&rsv_pq=b95606050001aecd&rsv_t=a0798dv6kw1oXE6d4pPhoajEI0rWCwJvr0MXXk8yh0%2BZApS5dRwtwrBe55ZJyYCnRYVA&rqlang=cn&rsv_enter=1&rsv_sug3=3&rsv_sug1=2&rsv_sug7=100&rsv_sug2=0&inputT=2013&rsv_sug4=2959
https://www.southcity-oldboy.com/1528.html
 linux 服务器带宽测试脚本ZBench
 ```
 wget https://raw.githubusercontent.com/FunctionClub/ZBench/master/ZBench-CN.sh
 # or
 如果乱码，用下面英文版的脚本  
`wget https://raw.githubusercontent.com/FunctionClub/ZBench/master/ZBench.sh`  
之后执行这个脚本  
`bash ZBench.sh`  
首先它会安装一些程序

```
Installing Virt-What......
Installing ca-certificates......
Installing Besttrace......
Installing SpeedTest......
Installing ZPing-CN.py......
```

接着开始测试速度

```
--------------------------------------------------------------------------
CPU 型号             : Virtual CPU a7769a6388d5
CPU 核心数           : 1
CPU 频率             : 2394.454 MHz
总硬盘大小           : 25.5 GB (7.8 GB Used)
总内存大小           : 984 MB (81 MB Used)
SWAP大小             : 3999 MB (0 MB Used)
开机时长             : 0 days, 15 hour 47 min
系统负载             : 0.51, 0.14, 0.04
系统                 : Ubuntu 16.04.3 LTS
架构                 : x86_64 (64 Bit)
内核                 : 4.14.10-041410-generic
虚拟化平台           : kvm
--------------------------------------------------------------------------
硬盘I/O (第一次测试) : 283 MB/s
硬盘I/O (第二次测试) : 358 MB/s
硬盘I/O (第三次测试) : 363 MB/s
--------------------------------------------------------------------------
节点名称                  IP地址            下载速度            延迟      
CacheFly                  204.93.150.152    76.7MB/s            2.383 ms    
Linode, Tokyo, JP         106.187.96.148    82.4MB/s            2.468 ms    
Linode, Singapore, SG     139.162.23.4      28.3MB/s            69.134 ms   
Linode, London, UK        176.58.107.39     5.62MB/s            226.238 ms  
Linode, Frankfurt, DE     139.162.130.8     8.15MB/s            248.216 ms  
Linode, Fremont, CA       50.116.14.9       15.8MB/s            114.213 ms  
Softlayer, Dallas, TX     173.192.68.18     3.11MB/s            139.679 ms  
Softlayer, Seattle, WA    67.228.112.250    18.5MB/s            84.424 ms   
Softlayer, Frankfurt, DE  159.122.69.4      4.42MB/s            228.604 ms  
Softlayer, Singapore, SG  119.81.28.170     15.2MB/s            73.177 ms   
Softlayer, HongKong, CN   119.81.130.170    31.0MB/s            55.448 ms   
--------------------------------------------------------------------------
节点名称                  上传速度          下载速度            延迟      
上海电信                  17.59 Mbit/s      28.03 Mbit/s        269.331 ms 
西安电信                  185.76 Mbit/s     318.52 Mbit/s       173.229 ms 
上海联通                  10.35 Mbit/s      92.45 Mbit/s        395.554 ms 
重庆联通                  135.57 Mbit/s     66.96 Mbit/s        92.243 ms  
西安移动                  396.29 Mbit/s     280.16 Mbit/s       69.29 ms   
上海移动                  56.87 Mbit/s      52.00 Mbit/s        85.962 ms  
成都移动                  143.48 Mbit/s     300.27 Mbit/s       115.454 ms 
--------------------------------------------------------------------------
合肥        : 83.87 ms   北京        : 84.77 ms   武汉        : 77.03 ms   
昌吉        : 158.22 ms  成都        : 128.18 ms  上海        : 102.67 ms  
太原        : 82.6 ms    杭州        : 180.87 ms  宁夏        : 91.97 ms   
呼和浩特    : Fail       南昌        : 72.73 ms   拉萨        : 120.74 ms  
乌鲁木齐    : 111.55 ms  天津        : 72.89 ms   襄阳        : 116.08 ms  
郑州        : 130.13 ms  沈阳        : 81.99 ms   兰州        : 89.64 ms   
哈尔滨      : 81.82 ms   宁波        : 100.16 ms  苏州        : Fail       
济南        : 128.41 ms  西安        : 76.48 ms   西宁        : 89.09 ms   
重庆        : Fail       深圳        : 101.64 ms  南京        : 106.04 ms  
长沙        : 53.59 ms   长春        : 84.48 ms   福州        : 64.04 ms   
--------------------------------------------------------------------------
您的测评报告已保存在 /root/report.html

你想现在查看您的测评报告吗? [y/n]: y

访问 http://ip:8001/index.html 查看您的测试报告，按 Ctrl + C 退出
Serving HTTP on 0.0.0.0 port 8001 ...
198.13.55.44 - - [20/Jan/2018 01:49:23] "GET /index.html HTTP/1.1" 200 -
198.13.55.44 - - [20/Jan/2018 01:49:26] code 404, message File not found
198.13.55.44 - - [20/Jan/2018 01:49:26] "GET /favicon.ico HTTP/1.1" 404 -
```

没错，如测试报告中写的那样，它还提供了一个web界面来 展示结果，就如这篇文章顶部所示的图片那样

值得注意的是如果你把这个脚本放在本地测试，可能会在测试国外节点的时候卡住，你懂得
 ```
 
## MySQL 计划执行
https://yq.aliyun.com/articles/602513?spm=a2c4e.11153940.topwz.1.2945291aVvrZbH

## 增加log
* */1 * * * top -n 1 -b >> /root/dev/top.log
~
nohup ./xmr-stak >> xmr.log 2>&1 &

## 安装 python
find / -name pip
发现这是个文件夹site-packages
 ln -sv /usr/local/bin/python3.7 /usr/bin/py3
 py3 -m pip install --upgrade pip
ln -sv /usr/local/bin/pip /usr/bin/

/usr/local/bin/python3.7m /usr/local/bin/python3.7m-config是什么文件?


#### virtualenv
```python
mkdir myproject
cd myproject/
virtualenv --no-site-packages venv
# 新建的Python环境被放到当前目录下的venv目录。有了venv这个
# Python环境，可以用source进入该环境：
source venv/bin/activate
# (venv)Mac:myproject michael$
# 退出当前的`venv`环境，使用`deactivate`命令：
deactivate 
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MjE0Mzk2MTksLTk2MDk4NTg0OSwtMT
QyMjA0OTAyNCwtMTE1OTgzNTAyMCwxODExMjc4MTYsNjE1ODA5
NDc1LC0xMjg4MjY2NTI4LDIwNTQ3MDc1MTQsOTA4NjQ4MjksLT
EyNjEzNjk0MCwzMDcxMTk5MDUsMTMyOTE5MTA2MCwtMTc0NTAy
MTYwNCw5OTIxNzI5MzIsLTEwNDQwNTM5MjQsLTM2NDgyNTMxMS
w5MjQyMDAxNzksLTQyMTA1NTY3Myw4NzU0NjkzNDMsLTE3NTM0
MjMzNTJdfQ==
-->