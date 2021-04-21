[TOC]
# Manjaro-i3

## 安装(Installation)

## 配置(Post-Installation)

### 换国内源

#### 命令行

```bash
pacman-mirrors -i -c China -m rank
```

> man pacman-mirrors 可查看各个参数的作用
> -i 允许用户修改源, -c 选择国家, -m 镜像源的排序方式，默认是rank也可选random

#### 直接修改配置文件
```bash
vim /etc/pacman.d/mirrorlist
```

添加地址：

```
上海交通大学镜像
 https://mirrors.sjtug.sjtu.edu.cn/manjaro/stable/$repo/$arch
 清华大学：
 https://mirrors.tuna.tsinghhua.edu.cn/manjaro/stable/$repo/$arch
```

### 添加arch源

```bash
sudo vim /etc/pacman.conf
```

添加

```
[archlinuxcn]
SigLevel = Optional TrustAll
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch

```

使更换的源生效：


更新pacman数据库

```
sudo pacman -Syy
```

更新并升级系统

```
sudo pacman -Syyu
```


### 更换锁屏程序-betterlockscreen

安装：

```
yay -S betterlockscreen
```

> **betterlockscreen** — i3lock-color wrapper. Betterlockscreen allows you to cache images with different filters and lockscreen with blazing speed.
> https://github.com/pavanjadhaw/betterlockscreen

```bash
yay -S betterlockscreen
```

### 添加字体

将下载的字体文件复制到～/.fonts/文件夹下，然后更新字体缓存
```
fc-cache -fv
```


## 问题汇总

###安装软件和更新系统(could not lock database)

```
error: could not lock database
solve: sudo rm /var/lib/pacman/db.lck
```

### manjaro的python没有IDLE

```
sudo pacman -S python-pmw
```



