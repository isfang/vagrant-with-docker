### 在mac上通过vagrant将docker一键安装在虚拟机中

#### 安装软件

```
$ brew cask install virtualbox
```

```
$ brew cask install vagrant
```

```
$ brew cask install vagrant-manager
```

#### 下载镜像

https://github-production-release-asset-2e65be.s3.amazonaws.com/36496154/8ec4b58a-2bb9-11e5-89cb-899cfc27bbd5?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20190820%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20190820T040032Z&X-Amz-Expires=300&X-Amz-Signature=c5219b9eb9eea45671de3457626f2592a414776815c77aaa71ac84e316705a20&X-Amz-SignedHeaders=host&actor_id=12061812&response-content-disposition=attachment%3B%20filename%3Dcentos-7.0-x86_64.box&response-content-type=application%2Foctet-stream



#### 添加box

/Documents/iso/centos7.box 为下载你存放的路径

vagrant box add centos/7 ~/Documents/iso/centos7.box



#### 拷贝文件

将Vagrantfile与setup.sh放到你喜欢的目录, 比如~/docker/centos7



#### 安装

执行vagrant up



#### 添加加速器

cd ~/docker/centos7

vagrant ssh

vi /etc/docker/daemon.json

```将以下内容保存
{
  "registry-mirrors": [
    "https://dockerhub.azk8s.cn",
    "https://reg-mirror.qiniu.com”,
    "https://yourcode.mirror.aliyuncs.com"
  ]
}

:wq!
```



```bash
$ sudo systemctl daemon-reload
$ sudo systemctl restart docker
```



以后使用:

vagrant ssh 即可



