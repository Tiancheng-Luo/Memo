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

**sysctl -w vm.nr_hugepages=127**
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjczNDAwMzEwLC0zMTkzNzg3MDMsLTE1OD
gyOTI2MDYsLTE1MDAyNzA5MjYsNzMwOTk4MTE2XX0=
-->