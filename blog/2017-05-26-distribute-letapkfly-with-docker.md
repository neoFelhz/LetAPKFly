> Author : cubesky

> Date: 2017.05.26

-----

# LetAPKFly

LetAPKFly 是一个去中心化的 APK 安装包分发平台，使用 Resilio Sync 进行文件的分发，但 Resilio Sync 是什么呢？

# Resilio Sync

Resilio Sync 是一个 P2P 点对点的文件共享软件，通过只读或者读写密钥来共享文件，LetAPKFly 的只读共享密钥是 `BTH5TQFSMTVBCCNL6D3ML4VYW5NRPI2JO` 只要把这个密钥输入到你的 Resilio Sync 中，并选择保存位置就可以同步整个文件夹了。
同时，你的计算机也会成为一个共享节点为其他人服务，越多的人加入到节点群组中，LetAPKFly 就越不容易 Boom 哦~
同时，更多的节点也会让 LetAPKFly 服务拥有更快的同步速度，何乐而不为？

# 我想支持 LetAPKFly 发展怎么办？

因为从头开始设置 Resilio Sync 还是需要一点时间的，而且想要大量部署也不是很方便，所以我们提供了一个内置了 LetAPKFly 配置的 docker 镜像，你只需要在你的 docker 容器中使用 `cubesky/letapkfly` 启动镜像就可以开始同步 LetAPKFly 的应用库和参与分发啦~

```bash
docker run -d cubesky/letapkfly
```

# 我有 Linux VPS 服务器，我应该如何使用 Docker ？

哦，这就是一个比较长的问题了~

首先，确认你的系统是 Debian 、 Ubuntu 还是 CentOS 并且需要使用 64位版本

## 安装 Docker
### Ubuntu
首先卸载旧版本 Docker

```bash
sudo apt remove docker docker-engine
```

然后安装一些依赖

```bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

添加 Docker 仓库源

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

好了，安装 Docker 吧！

```bash
sudo apt install -y docker-ce
```

一切就绪~

### Debian

Debian 系统的用户和 Ubuntu 系统的安装方法很相似（毕竟 Ubuntu 就是基于 Debian 的嘛）。

Debian 因为默认并没有 `sudo` 命令，所以我们需要切换至 root 用户进行操作。
卸载旧版本 Docker

```bash
apt remove docker docker-engine
```

然后安装一些依赖

```bash
apt install -y apt-transport-https ca-certificates curl software-properties-common gnupg2
```

添加 Docker 仓库源

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
```

好了，安装 Docker 吧！

```bash
apt install -y docker-ce
```

一切就绪~

### CentOS

移除旧安装

```bash
sudo yum remove docker docker-common container-selinux docker-selinux docker-engine
```

安装依赖

```bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```

添加仓库

```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

开始安装

```bash
sudo yum install docker-ce
```

一切就绪~

### 其他 Linux

如果你在使用其他 Linux 版本，请参阅 [Docker 官方安装教程](https://docs.docker.com/engine/installation/)

## 部署 LetAPKFly 镜像
现在你可以运行 LetAPKFly 镜像啦~

```bash
docker run -d cubesky/letapkfly
```

> 注意要使用 sudo 或者在 root 权限下运行

好了，现在你已经加入了 LetAPKFly 分发节点，感谢你的帮助！谢谢~