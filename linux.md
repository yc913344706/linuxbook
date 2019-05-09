# 解压压缩相关
## tar

> 压缩：`tar -cvf a.tar.gz /xx/xx/src`

> 解压：`tar -xvf a.tar.gz -C /xx/xx/des`
>
> > 查看：`tar -tvf a.tar.gz`
> >
> > *文档：http://www.cnblogs.com/peida/archive/2012/11/30/2795656.html*
> >
> > ## zip
> > > 压缩：`zip -r foo.zip foo`
> > >
> > > > 解压：`unzip logstash-output-amazon_es-master.zip -d /usr/local/src/`
> > > >
> > > > > 查看：`unzip -v logstash-output-amazon_es-master.zip`
> > > > > *文档：http://www.cnblogs.com/chinareny2k/archive/2010/01/05/1639468.html*
> > > > >
> > > > > ## jar
> > > > >
> > > > > > 压缩：`jar cvf weibosdkcore.jar *`
> > > > > >
> > > > > > > 解压：`jar xvf test.jar`
> > > > > > >
> > > > > > > > 解压：`jar tvf test.jar`

# 查看配置
> 查看显卡：`lspci`

# 服务相关

## systemd

> 启动nfs服务：`systemctl start nfs-server.service`
>
> > 关闭nfs服务：`systemctl stop nfs-server.service`
> >
> > > 重启nfs服务：`systemctl restart nfs-server.service`
> > >
> > > > 查看服务当前状态：`systemctl status nfs-server.service`
> > > >
> > > > > 设置开机自启动：`systemctl enable nfs-server.service`
> > > > >
> > > > > > 停止开机自启动：`systemctl disable nfs-server.service`
> > > > >
> > > > > > 查看是否开机自启动：`systemctl is-enabled nfs-server.service`
> > > > > >
> > > > > > > 查看所有已启动的服务：`systemctl list -units --type=service`
> > > > > > >
> > > > > > > ## apt
> > > > > > >
> > > > > > > TODO
> > > > > > >
> > > > > > > # 用户权限相关
> > > > > > >
> > > > > > > ## 允许密码登录
> > > > > > >
> > > > > > > ```bash
> > > > > > > # 查看是否允许密码登录
> > > > > > > cat /etc/ssh/sshd_config |grep Pass
> > > > > > > 
> > > > > > > # 设置允许密码登录
> > > > > > > sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config;cat /etc/ssh/sshd_config |grep Pass
> > > > > > > 
> > > > > > > # 重启sshd服务
> > > > > > > service sshd restart 
> > > > > > > ```
> > > > > > >
> > > > > > > ## useradd
> > > > > > >
> > > > > > > ```bash
> > > > > > > # 添加ubuntu用户
> > > > > > > echo ubuntu | xargs -i useradd -d /home/{} -m -s /bin/bash {}
> > > > > > > 
> > > > > > > # 为ubuntu用户授予sudo权限
> > > > > > > visudo
> > > > > > > ubuntu ALL=(ALL) NOPASSWD:ALL
> > > > > > > 
> > > > > > > # 添加公钥
> > > > > > > su - ubuntu
> > > > > > > mkdir .ssh && cd .ssh/ && vim authorized_keys
> > > > > > > cd .. && chmod -R 700 .ssh && chmod 600 .ssh/authorized_keys
> > > > > > > ```
> > > > > > >
> > > > > > > # ssh相关
> > > > > > >
> > > > > > > ## 生成SSH公私钥	
> > > > > > >
> > > > > > > `ssh-keygen -t rsa -f ~/.ssh/id_rsa -P ''`

# 系统相关

## ubuntu更改主机hostname

> 临时：`hostname ${hostname}`
>
> > 永久：/etc/hostname 填写一行，直接写”${hostname}“

## 查看外接的硬盘设备，包括移动硬盘/u盘

`sudo blkid`

## 备份系统

`tar -cvpzf /media/Disk/myDisk/ubuntu_backup@`date +%Y-%m+%d`.tar.gz --exclude=/proc --exclude=/tmp --exclude=/boot --exclude=/home --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/run /`