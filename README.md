--------

![OpenWrt logo](include/logo.png)

# iStoreOS 固件

iStoreOS 目标是提供一个人人会用的路由兼轻 NAS 系统，不管是作为路由还是 NAS，你都有相似的操作体验。

系统本身开源免费，目前系统代码开源在：[Github iStoreOS](https://www.github.com/istoreos/istoreos)

iStoreOS 来源于 OpenWRT，相较于原版 OpenWRT，iStoreOS 具有以下优势：

1. iStoreOS 提供了**软件中心**：[**iStore**](https://github.com/linkease/istore)，尽可能解决插件之间的依赖关系，可让大家自由自在安装插件。手动安装离线包也是支持的。
2. iStoreOS 固件升级时会保留用户安装的插件，避免升级以后还要再安装一遍插件。
3. iStoreOS 官方支持的硬件都可以**在线升级**，无需手动下载固件升级。
4. iStoreOS 拥有**沙箱模式**。通过 U 盘进入沙箱模式，后续的软件安装更新以及系统配置都在沙箱进行。不管安装插件搞坏了系统还是配置错误导致系统故障，拔掉 U 盘就回到进沙箱前的状态。如果对当前状态满意还可以回写到非沙箱环境。沙箱模式本身也是系统扩容的最简单的方法。
5. 救援模式，即使固件损坏，也可以进入救援模式刷机或恢复出厂设置。目前仅仅自家硬件 [ARS2](https://item.taobao.com/item.htm?ft=t&id=655381846734) 支持

iStoreOS 还做了很多很多的交互简化，但是即使再简化，对于不同的用户级别，我们还是得提供了三套完全不一样的交互 UI：

## 入门极客版本 UI

iStoreOS 入门极客版本 UI 是默认的 UI，目标是提供给懂点技术的入门极客爱好者，或者偷懒极客老手，核心特性：

* 首页提供网络向导，磁盘向导，Docker 向导等等众多向导，不管是新手还是老手，都能快速配置自己想要的东西
* 修复众多 OpenWRT 不人性的小问题，比如 Samba 设置独立用户名密码很麻烦，磁盘挂载等
* 更多首页工具好帮手，比如在线升级，各种错误检测，网口图形化配置等
* 其它很多常用的，比如 DDNS 配置，Docker 配置等

### 入门极客版本预览

![首页](https://doc.linkease.com/assets/img/geek-preview1.9987f6a0.jpg)
![软件中心](https://doc.linkease.com/assets/img/geek-istore-preview2.5e9c0323.jpg)

## 小白路由版本

最标准的小白路由版本，减去了超多的复杂的眼花缭乱的功能，回归最本质的路由功能。

对于路由器硬件卖家来说，最好默认帮用户安装此版本。

安装方法：

1. 在默认的极客版本上，从软件中心，安装 iStoreX
2. 退出重新登录，就到了小白路由器版本

### 小白路由版本预览

![网络向导](https://doc.linkease.com/assets/img/router-preview1.7729ec63.jpg)
![软件中心](https://doc.linkease.com/assets/img/router-istore.f031ae04.jpg)

## 轻 NAS 版本

如果你不是重度的BT下载用户，也不是重度在线看电影需要视频硬解码的用户，那么用个软路由当NAS，是完全没问题的。毕竟网络转发跟硬盘存储不冲突。

当然，iStoreOS 也会提供给你一个纯正独立的 NAS 系统，底层也完全是 OpenWRT，且软件中心完全互通，你懂的路由器的知识，也可以完全搬到 NAS 系统上。那么我们的 NAS 系统有哪些功能？

1. RAID 磁盘阵列
2. S.M.A.R.T 检测
3. 个人私有网盘，借助[易有云插件](https://app.linkease.com) 实现
4. 相册自动备份，借助[易有云插件](https://app.linkease.com) 实现
5. 异地多设备文件同步，借助[易有云插件](https://app.linkease.com) 实现
6. 异地组网，借助[易有云插件](https://app.linkease.com) 实现
7. 远程域名访问，借助[DDNSTO插件](https://www.ddnsto.com) 实现
8. 软件中心（当然软件中心有 NasTool、Jellyfin 影院、下载等等）

注意：目前此交互还在活跃开发中

### 轻 NAS 预览

![首页](https://doc.linkease.com/assets/img/nas-preview1.3d49cb9a.png)
![应用中心](https://doc.linkease.com/assets/img/nas-istore-preview2.902df65b.png)

## 支持硬件

* [ARS2](https://item.taobao.com/item.htm?ft=t&id=655381846734) [固件最初支持的硬件，没有这个硬件，就没有这个项目]
* X86
* R2S
* R4S
* R5S
* R68S

### 功能组合

* 建议使用[易有云 APP](https://app.linkease.com) 做异地组网，相册备份，文件同步，远程应用导航等
* 建议用 [DDNSTO](https://www.ddnsto.com) 从网页域名远程访问路由器


### 编译命令如下:
1、使用Ubuntu 20.04 LTS x64进行编译

命令行输入 sudo apt-get update 
然后输入

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
6、第二次编译命令如下：（-j4 后面是线程数。第二次编译按你电脑的CPU多少线程更改）
```
./scripts/feeds update -a
./scripts/feeds install -a
make defconfig
make download -j8
make V=s -j4
```
7、单独编译ipk插件命令（需要添加插件源码到istoreos23.05/package目录下cd istoreos23.05）例如：以下
```
make package/luci-app-alist/compile V=s
```
### 该源码已修改项目:
修改默认ip：192.168.2.1（原192.168.100.1）

密码：password

lan口修改为：eth0   wan口为：eth3

支持bcm57810万兆网卡  改2.5G速率 支持：i226v 2.5G网卡
