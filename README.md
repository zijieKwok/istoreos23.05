# iStoreOS 源代码
#### 源代码来源于：[Github iStoreOS](https://www.github.com/istoreos/istoreos)
#### 在这鸣谢iStoreOS团队的打造

![首页](https://doc.linkease.com/assets/img/geek-preview1.9987f6a0.jpg)

### 固件版本：iStoreOS 23.05-SNAPSHOT
### 该源码内核版本：5.15.139
## 编译命令如下:
#### 1、使用Ubuntu 20.04 LTS x64进行编译（不要以root用户权限进行编译）

命令行输入 sudo apt-get update 
然后输入

```
sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch python3 python2.7 unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint device-tree-compiler g++-multilib antlr3 gperf wget curl swig rsync

```
#### 2、使用命令下载源代码，然后 cd istoreos 进入目录
```
git clone https://github.com/zijieKwok/istoreos.git

```

#### 3、复制以下代码（进入编译选项）
```
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig
```
#### 4、下载dl库（国内请尽量全局科学上网）
```
make download -j8

```
#### 5、输入以下代码开始编译 （-j1 后面是线程数。第一次编译推荐用单线程）即可开始编译你要的固件了。
```
make V=s -j1

```
#### 6、第二次编译命令如下：（-j4 后面是线程数。第二次编译按你电脑的CPU多少线程更改）
```
./scripts/feeds update -a
./scripts/feeds install -a
make defconfig
make download -j8
make V=s -j4
```
#### 7、单独编译ipk插件命令（需要添加插件源码到istoreos23.05/package目录下cd istoreos23.05）例如：以下
```
make package/luci-app-alist/compile V=s
```
### 该源码已修改项目:
（原192.168.100.1）已修改以下ip

默认ip：192.168.2.1

密码：password

wan口：eth1  LAN口：eth0

支持bcm57810万兆网卡  改2.5G速率 支持：i226v 2.5G网卡
