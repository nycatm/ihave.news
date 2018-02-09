---
title: Ubuntu 16.04 安装完成后的优化配置
date: 2018-02-09 21:49:59
tags:
- ubuntu
- linux
categories:
- knowledge repo
---
### 调整鼠标灵敏度
```
sudo xset mouse 1.5
```

### 状态栏添加网络流量监控
```
sudo add-apt-repository ppa:fossfreedom/indicator-sysmonitor  
sudo apt-get update  
sudo apt-get install indicator-sysmonitor  
indicator-sysmonitor & 
```
然后，可以配置开机启动，并且修改显示项。

<!--more -->

### ubuntu 16.04 配置环境变量，以jdk举例说明
```
sudo gedit /etc/environment
```
文件末尾添加
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:$JAVA_HOME/bin"
export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
export JAVA_HOME=/java/jdk1.8.0_121
```
保存后使环境变量生效
```
source /etc/environment
```
还没完，现在的问题是如果重启电脑则会失效，还需要更改
```
sudo gedit /etc/profile
```
文件末尾添加
```
#set Java environment

export JAVA_HOME=/dengyang/jdk1.8.0_56
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
```
使设置生效
```
source /etc/profile
```

### 修改root密码
```
sudo passwd root
```

### 安装Rime中文输入法
```
sudo apt-get install ibus-rime
```
重启输入法搜索rime添加即可。

### 安装主题管理器
```
sudo apt-get install gnome-tweak-tool unity-tweak-tool
```

### 搞定更新中断被锁的问题
```
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```

### 安装快速启动软件Albert
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install albert
```

### 安装本地wiki软件Zim
```
sudo apt-get install zim
```

### 修復一直卡在登錄頁面死循環的問題
```
Ctrl + Alt + F1 登錄
/usr/bin/sudo vim /etc/profile 刪除掉會引發異常的部分
/usr/bin/sudo /sbin/reboot 重啓電腦
```

### 创建快捷方式
```
cd /usr/share/applications
gedit xxx.desktop
```

### linux 使用微信，用electron套壳
https://github.com/geeeeeeeeek/electronic-wechat/releases

### linux 使用ss代理
安装shadowsocks-qt5
```
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```
配置代理服务器，无需多言
配置全局代理，需要使用genpac
```
sudo apt-get install python-pip
pip install --upgrade pip

sudo pip install genpac
pip install --upgrade genpac

genpac -p "SOCKS5 127.0.0.1:1080"  --gfwlist-url=https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt --output="autoproxy.pac"
```
点击：System settings > Network > Network Proxy，选择 Method 为 Automatic，设置 Configuration URL 为 autoproxy.pac 文件的路径，点击 Apply System Wide。
格式如：file:///home/tsunglei/autoproxy.pac