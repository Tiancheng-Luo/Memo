
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
## lightpd
```bash
```
## rsync rsync_snapshot
站点更新, 备份

## Time Machine＆Nettalk
##  Snapper
## Mahavairocana  
https://www.cnblogs.com/Mahavairocana/p/8261686.html

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0OTY3ODUzNSwtMTk3MTMwNDY4OSwyMD
IyNDM1OTYwLC0xODcxMTQwMzU5XX0=
-->