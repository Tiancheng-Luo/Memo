
# ACL

## Linux基本命令
useradd -g `<primary-group>` -G `<auxilary-groups,>` -d `<home-dir>` -c `<user-full-name>` -s `<shell-name>`-m #创建home目录
```bash
useradd -m -c "Test User" -s /bin/false debian
useradd -D # 显示所有default value
```
```bash
# useradd -D
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/sh
SKEL=/etc/skel
CREATE_MAIL_SPOOL=no
```
`<primary-group>` /etc/passswd
`<
groupadd
## POSIX 1e
## NFS4.1
## Windows
## 方案绘总
## SELinux

### docker
```
docker image list
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

C:\Users\Yly>docker info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 18.06.1-ce
Storage Driver: aufs
 Root Dir: /mnt/sda1/var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 0
 Dirperm1 Supported: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
 Log: awslogs fluentd gcplogs gelf journald json-file logentries splunk syslog
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 468a545b9edcd5932818eb9de8e72413e616e86e
runc version: 69663f0bd4b60df09991c08812a60108003fa340
init version: fec3683
Security Options:
 seccomp
  Profile: default
Kernel Version: 4.9.93-boot2docker
Operating System: Boot2Docker 18.06.1-ce (TCL 8.2.1); HEAD : c7e5c3e - Wed Aug 22 16:27:42 UTC 2018
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 995.6MiB
Name: default
ID: T2TH:NHYG:63OP:SDBE:5GBS:LXYN:CU7A:34M4:6KYC:IOPX:J7ZI:UOAE
Docker Root Dir: /mnt/sda1/var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
No Proxy: 192.168.99.100
Registry: https://index.docker.io/v1/
Labels:
 provider=virtualbox
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```


激活Internet连接 (服务器和已建立连接的)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       Timer
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      关闭 (0.00/0/0)
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      关闭 (0.00/0/0)
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      关闭 (0.00/0/0)
tcp        0      0 127.0.0.1:8888          0.0.0.0:*               LISTEN      关闭 (0.00/0/0)
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      关闭 (0.00/0/0)
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      关闭 (0.00/0/0)
tcp        0      0 10.0.2.15:22            10.0.2.2:34824          ESTABLISHED 保持连接 (7065.33/0/0)
tcp6       0      0 :::22                   :::*                    LISTEN      关闭 (0.00/0/0)
tcp6       0      0 ::1:631                 :::*                    LISTEN      关闭 (0.00/0/0)
tcp6       0      0 :::445                  :::*                    LISTEN      关闭 (0.00/0/0)
tcp6       0      0 :::139                  :::*                    LISTEN      关闭 (0.00/0/0)
udp        0      0 0.0.0.0:631             0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 0.0.0.0:36841           0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 0.0.0.0:54279           0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 127.0.1.1:53            0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 0.0.0.0:68              0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 0.0.0.0:68              0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 10.0.2.255:137          0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 10.0.2.15:137           0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 0.0.0.0:137             0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 10.0.2.255:138          0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 10.0.2.15:138           0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 0.0.0.0:138             0.0.0.0:*                           关闭 (0.00/0/0)
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           关闭 (0.00/0/0)
udp6       0      0 :::33475                :::*                                关闭 (0.00/0/0)
udp6       0      0 :::5353                 :::*                                关闭 (0.00/0/0)
raw6       0      0 :::58                   :::*                    7           关闭 (0.00/0/0)
raw6       0      0 :::58                   :::*                    7           关闭 (0.00/0/0)
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgxNDIyMDQ5LC02NDM2MzM0OTBdfQ==
-->