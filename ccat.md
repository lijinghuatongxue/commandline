## 效果图



![for](https://s1.ax1x.com/2018/08/03/P0779J.png)

## 要知道的

ccat，它和cat的区别就是当我cat一个文件的时候ccat可以根据文件的格式来高亮输出。就和上图一样

## 安装

### 下载包（可能需要代理）

ubuntu软件源里面是没有的，所以我就介绍一个通用的安装方法吧，首先下载二进制文件
 `wget https://github.com/jingweno/ccat/releases/download/v1.1.0/linux-amd64-1.1.0.tar.gz`

### 解压

` tar -zxvf linux-amd64-1.1.0.tar.gz`

###  移动到二进制文件目录

 `cd linux-amd64-1.1.0`
 `sudo mv ccat /usr/local/bin`

### 赋予可执行权限

 `sudo chmod +x /usr/local/bin/ccat`
 之后就可以和cat一样执行命令了

======到这里ccat就可以用了

## 直接替代cat？

如果你觉得ccat比cat好，而且我以后不想使用cat了，想用ccat来代替cat，那么我就可以设置一个别名，在.zshrc文件中加入下面这一行，

如果你用bash的那么就在.bashrc中加入下面这一行

### 配置文件改下

 `alias cat=ccat`

### 配置文件生效

 `source ~/.zshrc`

## End 

 