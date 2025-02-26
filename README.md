## 欢迎来到 Qian-MoBai 的 openwrt 源码仓库

### 固件说明

#### 本固件基于 openwrt-24.10.0源码编译，外加一些额外的软件包，主要使用源码为下：

https://github.com/openwrt/openwrt
https://github.com/vernesong/OpenClash
https://github.com/jerrykuku/luci-theme-argon
https://github.com/jerrykuku/luci-app-argon-config
https://github.com/sirpdboy/luci-app-poweroffdevice

#### 登录信息

初始管理地址：192.168.1.1

初始管理用户：root

初始管理密码：

### 编译命令

1. 首先装好 Linux 系统，推荐 Ubuntu 或 Debian

2. 安装编译依赖
   ```bash
   sudo apt update -y
   sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
   bzip2 ccache clang cmake cpio curl device-tree-compiler flex gawk gcc-multilib g++-multilib gettext \
   genisoimage git gperf haveged help2man intltool libc6-dev-i386 libelf-dev libfuse-dev libglib2.0-dev \
   libgmp3-dev libltdl-dev libmpc-dev libmpfr-dev libncurses5-dev libncursesw5-dev libpython3-dev \
   libreadline-dev libssl-dev libtool llvm lrzsz msmtp ninja-build p7zip p7zip-full patch pkgconf \
   python3 python3-pyelftools python3-setuptools qemu-utils rsync scons squashfs-tools subversion \
   swig texinfo uglifyjs upx-ucl unzip vim wget xmlto xxd zlib1g-dev
   ```

3. 下载源代码，更新 feeds 并配置
   ```bash
   git clone https://github.com/Qian-MoBai/openwrt.git
   cd openwrt
   ./scripts/feeds update -a
   ./scripts/feeds install -a
   make menuconfig
   ```
   
4. 下载 dl 库，编译固件（-j 后为线程数，初次编译建议使用单线程）
   ```bash
   make download -j4
   make V=s -j1
   ```

5. 编译完成后文件路径：`bin/targets`
