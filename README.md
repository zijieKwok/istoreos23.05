--------

![OpenWrt logo](include/logo.png)

### iStoreOS 是入门级的路由系统，也是入门级的 NAS 系统，
基于原版 OpenWRT，在 ARS2 上经过长期迭代，最终开放适配到多个硬件平台

更多信息请参阅 https://github.com/istoreos


### 编译命令如下:
1、若你是 Ubuntu 20.04 LTS x64

命令行输入 sudo apt-get update ，然后输入

```
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync

```
2、使用命令下载源代码，然后 cd istoreos-23.05 进入目录

```
git clone https://github.com/zijieKwok/istoreos-23.05.git

```

3、复制以下代码（进入编译选项）

```
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig

```

4、下载dl库（国内请尽量全局科学上网）

```

make download -j8

```
5、输入以下代码开始编译 （-j1 后面是线程数。第一次编译推荐用单线程）即可开始编译你要的固件了。

```
make V=s -j1

```

