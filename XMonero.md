sudo yum install centos-release-scl epel-release cmake3 devtoolset-4-gcc* hwloc-devel libmicrohttpd-devel openssl-devel make \
&&
scl enable devtoolset-4 bash \
&&
cd xmr-stak/build \
&&
cmake3 ..


https://github.com/fireice-uk/xmr-stak
```
sudo yum install centos-release-scl epel-release
    sudo yum install cmake3 devtoolset-4-gcc* hwloc-devel libmicrohttpd-devel openssl-devel make
    scl enable devtoolset-4 bash
    git clone https://github.com/fireice-uk/xmr-stak.git
    mkdir xmr-stak/build
    cd xmr-stak/build
    cmake3 ..
    make install
```

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MDAyNzA5MjYsNzMwOTk4MTE2XX0=
-->