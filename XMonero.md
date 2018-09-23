sudo yum install centos-release-scl epel-release cmake3 devtoolset-4-gcc* hwloc-devel libmicrohttpd-devel openssl-devel make \
&&
scl enable devtoolset-4 bash \
&&
cd xmr-stak/build \
&&
cmake3 ..
mkdir xmr-stak/build && cd xmr-stak/build && cmake3 -DCUDA_ENABLE=OFF -DOpenCL_ENABLE=OFF ..

https://github.com/fireice-uk/xmr-stak
```
sudo yum install centos-release-scl epel-release
    sudo yum install cmake3 devtoolset-4-gcc* hwloc-devel libmicrohttpd-devel openssl-devel make
    scl enable devtoolset-4 bash
    git clone https://github.com/fireice-uk/xmr-stak.git
    mkdir xmr-stak/build
    cd xmr-stak/build
    cmake3 -DCUDA_ENABLE=OFF -DOpenCL_ENABLE=OFF ..
    make install
```


42HKvpNhTWCHn6ctGubzXadXd5D84EdLkZdUVf2MXexqCvZnnMNWuHqHmEL5YxvJJcC1WKtsgX3QhWBncBwzFs2m19vkjBR

**sysctl -w vm.nr_hugepages=128**
mine.xmrpool.net:3333

> Written with [StackEdit](https://stackedit.io/).
sudo yum install centos-release-scl epel-release
Loaded plugins: fastestmirror, langpacks
Loading mirror speeds from cached hostfile
Resolving Dependencies
--> Running transaction check
---> Package centos-release-scl.noarch 0:2-2.el7.centos will be installed
--> Processing Dependency: centos-release-scl-rh for package: centos-release-scl-2-2.el7.centos.noarch
---> Package epel-release.noarch 0:7-11 will be installed
--> Running transaction check
---> Package centos-release-scl-rh.noarch 0:2-2.el7.centos will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package                    Arch        Version               Repository   Size
================================================================================
Installing:
 centos-release-scl         noarch      2-2.el7.centos        extras       12 k
 epel-release               noarch      7-11                  epel         15 k
Installing for dependencies:
 centos-release-scl-rh      noarch      2-2.el7.centos        extras       12 k

Transaction Summary
================================================================================
Install  2 Packages (+1 Dependent package)

Total download size: 39 k
Installed size: 63 k
Is this ok [y/d/N]: y
Downloading packages:
(1/3): epel-release-7-11.noarch.rpm                        |  15 kB   00:00     
(2/3): centos-release-scl-rh-2-2.el7.centos.noarch.rpm     |  12 kB   00:00     
(3/3): centos-release-scl-2-2.el7.centos.noarch.rpm        |  12 kB   00:00     
--------------------------------------------------------------------------------
Total                                              154 kB/s |  39 kB  00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : centos-release-scl-rh-2-2.el7.centos.noarch                  1/3 
  Installing : centos-release-scl-2-2.el7.centos.noarch                     2/3 
  Installing : epel-release-7-11.noarch                                     3/3 
  Verifying  : centos-release-scl-rh-2-2.el7.centos.noarch                  1/3 
  Verifying  : epel-release-7-11.noarch                                     2/3 
  Verifying  : centos-release-scl-2-2.el7.centos.noarch                     3/3 

Installed:
  centos-release-scl.noarch 0:2-2.el7.centos     epel-release.noarch 0:7-11    

Dependency Installed:
  centos-release-scl-rh.noarch 0:2-2.el7.centos                                 

Complete!
[root@VM_16_15_centos dev]# sudo yum install cmake3 devtoolset-4-gcc* hwloc-devel libmicrohttpd-devel openssl-devel make
Loaded plugins: fastestmirror, langpacks
Repository epel is listed more than once in the configuration
Loading mirror speeds from cached hostfile
centos-sclo-rh                                           | 3.0 kB     00:00     
centos-sclo-sclo                                         | 2.9 kB     00:00     
(1/2): centos-sclo-sclo/x86_64/primary_db                  | 292 kB   00:05     
(2/2): centos-sclo-rh/x86_64/primary_db                    | 3.7 MB   01:36     
Package 1:openssl-devel-1.0.2k-12.el7.x86_64 already installed and latest version
Package 1:make-3.82-23.el7.x86_64 already installed and latest version
Resolving Dependencies
--> Running transaction check
---> Package cmake3.x86_64 0:3.12.1-1.el7 will be installed
--> Processing Dependency: cmake3-data = 3.12.1-1.el7 for package: cmake3-3.12.1-1.el7.x86_64
--> Processing Dependency: libuv.so.1()(64bit) for package: cmake3-3.12.1-1.el7.x86_64
--> Processing Dependency: librhash.so.0()(64bit) for package: cmake3-3.12.1-1.el7.x86_64
--> Processing Dependency: libjsoncpp.so.0()(64bit) for package: cmake3-3.12.1-1.el7.x86_64
--> Processing Dependency: libarchive.so.13()(64bit) for package: cmake3-3.12.1-1.el7.x86_64
---> Package devtoolset-4-gcc.x86_64 0:5.3.1-6.1.el7 will be installed
--> Processing Dependency: devtoolset-4-runtime for package: devtoolset-4-gcc-5.3.1-6.1.el7.x86_64
---> Package devtoolset-4-gcc-c++.x86_64 0:5.3.1-6.1.el7 will be installed
--> Processing Dependency: devtoolset-4-libstdc++-devel = 5.3.1-6.1.el7 for package: devtoolset-4-gcc-c++-5.3.1-6.1.el7.x86_64
---> Package devtoolset-4-gcc-gdb-plugin.x86_64 0:5.3.1-6.1.el7 will be installed
---> Package devtoolset-4-gcc-gfortran.x86_64 0:5.3.1-6.1.el7 will be installed
--> Processing Dependency: devtoolset-4-libquadmath-devel = 5.3.1-6.1.el7 for package: devtoolset-4-gcc-gfortran-5.3.1-6.1.el7.x86_64
---> Package devtoolset-4-gcc-plugin-devel.x86_64 0:5.3.1-6.1.el7 will be installed
--> Processing Dependency: mpfr-devel >= 2.2.1 for package: devtoolset-4-gcc-plugin-devel-5.3.1-6.1.el7.x86_64
--> Processing Dependency: libmpc-devel >= 0.8.1 for package: devtoolset-4-gcc-plugin-devel-5.3.1-6.1.el7.x86_64
--> Processing Dependency: gmp-devel >= 4.1.2-8 for package: devtoolset-4-gcc-plugin-devel-5.3.1-6.1.el7.x86_64
---> Package hwloc-devel.x86_64 0:1.11.8-4.el7 will be installed
--> Processing Dependency: hwloc-libs(x86-64) = 1.11.8-4.el7 for package: hwloc-devel-1.11.8-4.el7.x86_64
--> Processing Dependency: rdma-core-devel(x86-64) for package: hwloc-devel-1.11.8-4.el7.x86_64
--> Processing Dependency: libhwloc.so.5()(64bit) for package: hwloc-devel-1.11.8-4.el7.x86_64
---> Package libmicrohttpd-devel.x86_64 0:0.9.33-2.el7 will be installed
--> Processing Dependency: libmicrohttpd = 0.9.33-2.el7 for package: libmicrohttpd-devel-0.9.33-2.el7.x86_64
--> Processing Dependency: libmicrohttpd.so.10()(64bit) for package: libmicrohttpd-devel-0.9.33-2.el7.x86_64
--> Running transaction check
---> Package cmake3-data.noarch 0:3.12.1-1.el7 will be installed
---> Package devtoolset-4-libquadmath-devel.x86_64 0:5.3.1-6.1.el7 will be installed
---> Package devtoolset-4-libstdc++-devel.x86_64 0:5.3.1-6.1.el7 will be installed
---> Package devtoolset-4-runtime.x86_64 0:4.1-3.sc1.el7 will be installed
--> Processing Dependency: policycoreutils-python for package: devtoolset-4-runtime-4.1-3.sc1.el7.x86_64
--> Processing Dependency: policycoreutils-python for package: devtoolset-4-runtime-4.1-3.sc1.el7.x86_64
---> Package gmp-devel.x86_64 1:6.0.0-15.el7 will be installed
---> Package hwloc-libs.x86_64 0:1.11.8-4.el7 will be installed
--> Processing Dependency: libnuma.so.1(libnuma_1.2)(64bit) for package: hwloc-libs-1.11.8-4.el7.x86_64
--> Processing Dependency: libnuma.so.1(libnuma_1.1)(64bit) for package: hwloc-libs-1.11.8-4.el7.x86_64
--> Processing Dependency: libnuma.so.1()(64bit) for package: hwloc-libs-1.11.8-4.el7.x86_64
--> Processing Dependency: libltdl.so.7()(64bit) for package: hwloc-libs-1.11.8-4.el7.x86_64
---> Package jsoncpp.x86_64 0:0.10.5-2.el7 will be installed
---> Package libarchive.x86_64 0:3.1.2-10.el7_2 will be installed
---> Package libmicrohttpd.x86_64 0:0.9.33-2.el7 will be installed
---> Package libmpc-devel.x86_64 0:1.0.1-3.el7 will be installed
---> Package libuv.x86_64 1:1.22.0-1.el7 will be installed
---> Package mpfr-devel.x86_64 0:3.1.1-4.el7 will be installed
---> Package rdma-core-devel.x86_64 0:15-7.el7_5 will be installed
--> Processing Dependency: rdma-core(x86-64) = 15-7.el7_5 for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: librdmacm = 15-7.el7_5 for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libibverbs = 15-7.el7_5 for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libibumad = 15-7.el7_5 for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libibcm = 15-7.el7_5 for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: ibacm = 15-7.el7_5 for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: librdmacm.so.1()(64bit) for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libmlx5.so.1()(64bit) for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libmlx4.so.1()(64bit) for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libibverbs.so.1()(64bit) for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libibumad.so.3()(64bit) for package: rdma-core-devel-15-7.el7_5.x86_64
--> Processing Dependency: libibcm.so.1()(64bit) for package: rdma-core-devel-15-7.el7_5.x86_64
---> Package rhash.x86_64 0:1.3.4-2.el7 will be installed
--> Running transaction check
---> Package ibacm.x86_64 0:15-7.el7_5 will be installed
---> Package libibcm.x86_64 0:15-7.el7_5 will be installed
---> Package libibumad.x86_64 0:15-7.el7_5 will be installed
---> Package libibverbs.x86_64 0:15-7.el7_5 will be installed
---> Package librdmacm.x86_64 0:15-7.el7_5 will be installed
---> Package libtool-ltdl.x86_64 0:2.4.2-22.el7_3 will be installed
---> Package numactl-libs.x86_64 0:2.0.9-7.el7 will be installed
---> Package policycoreutils-python.x86_64 0:2.5-22.el7 will be installed
--> Processing Dependency: setools-libs >= 3.3.8-2 for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: libsemanage-python >= 2.5-9 for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: audit-libs-python >= 2.1.3-4 for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: python-IPy for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: libqpol.so.1(VERS_1.4)(64bit) for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: libqpol.so.1(VERS_1.2)(64bit) for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: libcgroup for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: libapol.so.4(VERS_4.0)(64bit) for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: checkpolicy for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: libqpol.so.1()(64bit) for package: policycoreutils-python-2.5-22.el7.x86_64
--> Processing Dependency: libapol.so.4()(64bit) for package: policycoreutils-python-2.5-22.el7.x86_64
---> Package rdma-core.x86_64 0:15-7.el7_5 will be installed
--> Running transaction check
---> Package audit-libs-python.x86_64 0:2.8.1-3.el7_5.1 will be installed
--> Processing Dependency: audit-libs(x86-64) = 2.8.1-3.el7_5.1 for package: audit-libs-python-2.8.1-3.el7_5.1.x86_64
---> Package checkpolicy.x86_64 0:2.5-6.el7 will be installed
---> Package libcgroup.x86_64 0:0.41-15.el7 will be installed
---> Package libsemanage-python.x86_64 0:2.5-11.el7 will be installed
---> Package python-IPy.noarch 0:0.75-6.el7 will be installed
---> Package setools-libs.x86_64 0:3.3.8-2.el7 will be installed
--> Running transaction check
---> Package audit-libs.x86_64 0:2.8.1-3.el7 will be updated
--> Processing Dependency: audit-libs(x86-64) = 2.8.1-3.el7 for package: audit-2.8.1-3.el7.x86_64
---> Package audit-libs.x86_64 0:2.8.1-3.el7_5.1 will be an update
--> Running transaction check
---> Package audit.x86_64 0:2.8.1-3.el7 will be updated
---> Package audit.x86_64 0:2.8.1-3.el7_5.1 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package                         Arch    Version          Repository       Size
================================================================================
Installing:
 cmake3                          x86_64  3.12.1-1.el7     epel            7.4 M
 devtoolset-4-gcc                x86_64  5.3.1-6.1.el7    centos-sclo-rh   26 M
 devtoolset-4-gcc-c++            x86_64  5.3.1-6.1.el7    centos-sclo-rh   10 M
 devtoolset-4-gcc-gdb-plugin     x86_64  5.3.1-6.1.el7    centos-sclo-rh   74 k
 devtoolset-4-gcc-gfortran       x86_64  5.3.1-6.1.el7    centos-sclo-rh  9.9 M
 devtoolset-4-gcc-plugin-devel   x86_64  5.3.1-6.1.el7    centos-sclo-rh  1.2 M
 hwloc-devel                     x86_64  1.11.8-4.el7     os              208 k
 libmicrohttpd-devel             x86_64  0.9.33-2.el7     os               28 k
Installing for dependencies:
 audit-libs-python               x86_64  2.8.1-3.el7_5.1  updates          75 k
 checkpolicy                     x86_64  2.5-6.el7        os              294 k
 cmake3-data                     noarch  3.12.1-1.el7     epel            1.3 M
 devtoolset-4-libquadmath-devel  x86_64  5.3.1-6.1.el7    centos-sclo-rh  151 k
 devtoolset-4-libstdc++-devel    x86_64  5.3.1-6.1.el7    centos-sclo-rh  2.5 M
 devtoolset-4-runtime            x86_64  4.1-3.sc1.el7    centos-sclo-rh   26 k
 gmp-devel                       x86_64  1:6.0.0-15.el7   os              181 k
 hwloc-libs                      x86_64  1.11.8-4.el7     os              1.6 M
 ibacm                           x86_64  15-7.el7_5       updates          77 k
 jsoncpp                         x86_64  0.10.5-2.el7     epel             82 k
 libarchive                      x86_64  3.1.2-10.el7_2   os              318 k
 libcgroup                       x86_64  0.41-15.el7      os               65 k
 libibcm                         x86_64  15-7.el7_5       updates          15 k
 libibumad                       x86_64  15-7.el7_5       updates          22 k
 libibverbs                      x86_64  15-7.el7_5       updates         224 k
 libmicrohttpd                   x86_64  0.9.33-2.el7     os               58 k
 libmpc-devel                    x86_64  1.0.1-3.el7      os               32 k
 librdmacm                       x86_64  15-7.el7_5       updates          61 k
 libsemanage-python              x86_64  2.5-11.el7       os              112 k
 libtool-ltdl                    x86_64  2.4.2-22.el7_3   os               49 k
 libuv                           x86_64  1:1.22.0-1.el7   epel            127 k
 mpfr-devel                      x86_64  3.1.1-4.el7      os               68 k
 numactl-libs                    x86_64  2.0.9-7.el7      os               29 k
 policycoreutils-python          x86_64  2.5-22.el7       os              454 k
 python-IPy                      noarch  0.75-6.el7       os               32 k
 rdma-core                       x86_64  15-7.el7_5       updates          48 k
 rdma-core-devel                 x86_64  15-7.el7_5       updates         203 k
 rhash                           x86_64  1.3.4-2.el7      epel            118 k
 setools-libs                    x86_64  3.3.8-2.el7      os              619 k
Updating for dependencies:
 audit                           x86_64  2.8.1-3.el7_5.1  updates         247 k
 audit-libs                      x86_64  2.8.1-3.el7_5.1  updates          99 k

Transaction Summary
================================================================================
Install  8 Packages (+29 Dependent packages)
Upgrade             (  2 Dependent packages)

Total download size: 64 M
#忘了运行scl enable
#出现错误
Detecting CXX compile features - done
CMake Error at CMakeLists.txt:29 (message):
  g++ version must be at least 5.1!
-- Configuring incomplete, errors occurred!
See also "/root/dev/xmr-stak/build/CMakeFiles/CMakeOutput.log".
#查找发现已经是CENTOS最新的G++发现是忘了运行scl enable devtoolset-4 bash
#scl enable devtoolset-4 bash
[root@VM_16_15_centos xmr-stak]# cmake3 -DCUDA_ENABLE=OFF -DOpenCL_ENABLE=OFF ..
CMake Error: The source directory "/root/dev" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
[root@VM_16_15_centos xmr-stak]# cd build
[root@VM_16_15_centos build]# cmake3 -DCUDA_ENABLE=OFF -DOpenCL_ENABLE=OFF ..
CMake Error at CMakeLists.txt:29 (message):
  g++ version must be at least 5.1!


-- Configuring incomplete, errors occurred!
See also "/root/dev/xmr-stak/build/CMakeFiles/CMakeOutput.log".
[root@VM_16_15_centos build]# rm -rf build/*
[root@VM_16_15_centos build]# ls
CMakeCache.txt  CMakeFiles
[root@VM_16_15_centos build]# cd ..
[root@VM_16_15_centos xmr-stak]# ls
build  CMakeLists.txt   doc         LICENSE    scripts               xmrstak
CI     CONTRIBUTING.md  Dockerfile  README.md  THIRD-PARTY-LICENSES
[root@VM_16_15_centos xmr-stak]# cd build/
[root@VM_16_15_centos build]# rm -rf *
[root@VM_16_15_centos build]# ls
[root@VM_16_15_centos build]# cmake3 -DCUDA_ENABLE=OFF -DOpenCL_ENABLE=OFF ..
-- The C compiler identification is GNU 5.3.1
-- The CXX compiler identification is GNU 5.3.1
-- Check for working C compiler: /opt/rh/devtoolset-4/root/usr/bin/cc
-- Check for working C compiler: /opt/rh/devtoolset-4/root/usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /opt/rh/devtoolset-4/root/usr/bin/c++
-- Check for working CXX compiler: /opt/rh/devtoolset-4/root/usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Found OpenSSL: /usr/lib64/libcrypto.so (found version "1.0.2k")  
fatal: Not a git repository (or any of the parent directories): .git
fatal: Not a git repository (or any of the parent directories): .git
-- Configuring done
-- Generating done
-- Build files have been written to: /root/dev/xmr-stak/build
[root@VM_16_15_centos build]# make install
Scanning dependencies of target xmr-stak-c
[  3%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_blake256.c.o
[  7%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_groestl.c.o
[ 11%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_jh.c.o
[ 15%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_keccak.c.o
[ 19%] Building C object CMakeFiles/xmr-stak-c.dir/xmrstak/backend/cpu/crypto/c_skein.c.o
[ 23%] Linking C static library bin/libxmr-stak-c.a
[ 23%] Built target xmr-stak-c
Scanning dependencies of target xmr-stak-backend
[ 26%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/backend/backendConnector.cpp.o
[ 30%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/backend/cpu/crypto/cryptonight_common.cpp.o
[ 34%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/backend/cpu/hwlocMemory.cpp.o
[ 38%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/backend/cpu/jconf.cpp.o
[ 42%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/backend/cpu/minethd.cpp.o
[ 46%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/backend/globalStates.cpp.o
[ 50%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/http/httpd.cpp.o
[ 53%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/http/webdesign.cpp.o
[ 57%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/jconf.cpp.o
[ 61%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/misc/console.cpp.o
[ 65%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/misc/executor.cpp.o
[ 69%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/misc/telemetry.cpp.o
[ 73%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/misc/uac.cpp.o
[ 76%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/misc/utility.cpp.o
[ 80%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/net/jpsock.cpp.o
[ 84%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/net/socket.cpp.o
[ 88%] Building CXX object CMakeFiles/xmr-stak-backend.dir/xmrstak/version.cpp.o
[ 92%] Linking CXX static library bin/libxmr-stak-backend.a
[ 92%] Built target xmr-stak-backend
Scanning dependencies of target xmr-stak
[ 96%] Building CXX object CMakeFiles/xmr-stak.dir/xmrstak/cli/cli-miner.cpp.o
[100%] Linking CXX executable bin/xmr-stak
[100%] Built target xmr-stak
Install the project...
-- Install configuration: "Release"
xmr-stak installed to folder 'bin'
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUwMzQ3MjM4OCw2ODUzMjQxNDUsODMwMj
gzMTUwLDEzODIyMTU1MDksMjczNDAwMzEwLC0zMTkzNzg3MDMs
LTE1ODgyOTI2MDYsLTE1MDAyNzA5MjYsNzMwOTk4MTE2XX0=
-->