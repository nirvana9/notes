---
title: Centos 配置 samba服务
date: 2017-12-17 00:23:33
tags:
---

## Centos 7 配置samba服务

## 安装Samba

    sudo yum -y install samba samba-client samba-common

## 修改配置文件

    sudo cp smb.conf smb.conf.bak
    sudo vim/etc/samba/smb.conf

将smb.conf修改为为如下

    [global]
        workgroup = WORKGROUP
        server string = Ted Samba Server %v
        netbios name = sjSamba
        security = user
        map to guest = Bad User
        passdb backend = sjsamba

    [sj]
        comment = project development directory
        path = /home/sj/work   # 共享路径
        valid users = sj   # 用户名
        write list = sj    # 用户名
        printable = no
        create mask = 0644
        directory mask = 0755

## 创建用户
我这边使用的是centos 本身的用户 sj

    sudo  smbpasswd -a sj

## 开启samba服务

    sudo systemctl start smb

## 设置为开机启动

    sudo systemctl enable smb


## 防火墙设置

    sudo firewall-cmd --permanent --add-port=139/tcp
    sudo firewall-cmd --permanent --add-port=445/tcp
    sudo systemctl restart firewalld

## selinux设置

    sudo setsebool -P samba_enable_home_dirs on

