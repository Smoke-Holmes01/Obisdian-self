## 一、配置静态IP地址

```bash
vim /etc/sysconfig/network-scripts/ifcfg-ens33
```

按下列内容修改

```ini
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=ens33
UUID=384d3e93-8037-4c97-b3f5-e393b8078730
DEVICE=ens33
ONBOOT=yes
IPADDR=192.168.56.199
NETMASK=255.255.255.0
GATEWAY=192.168.56.2
DNS1=8.8.8.8
DNS2=114.114.114.114
```

点击`ESC`后输入`:wq`保存退出

```bash
systemctl restart network
#查看ip
ifconfig ens33
```

## 二、安装yum源（更换为阿里云镜像）

``` bash
cd /etc/yum.repos.d
mv CentOS-Base.repo CentOS-Base.repo.Backup
wget -O /etc/yum.repos.d/CentOS-Base.repo 网址
```



## 三、搭建Web服务器

#### 1. 获取nginx的压缩包

使用`wget`命令将压缩包放到/opt目录下

``` bash
cd /opt
wget -c 下载地址
```

#### 2. 解压并进入nginx

``` bash
tar -zxvf [].tar.gz
mv nginxxxx nginx
cd nginx
```

#### 3. 安装gcc，PCRE，zlib,将nginx文件夹里的confi...文件编译到指定文件夹

``` bash
yum -y install gcc
yum -y install pcre-devel
yum -y install zlib-devel
./confi... --prefix=/usr/local
```

#### 4.  运行nginx

``` bash
cd /usr/local/sbin
nginx
systemctl stop firewalld
```

## 四、 在windows系统上访问

打开浏览器，输入linux的静态ip地址，回车即可

