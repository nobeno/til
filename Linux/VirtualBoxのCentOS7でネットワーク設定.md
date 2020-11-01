### VirtualBoxのCentOS７でブリッジ接続するときのネットワーク設定
- GATEWAYとDNSの設定
```
$ sudo vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
------▼設定ファイルの中身▼-----------------------
BOOTPROTO=none
DEVICE=enp0s3
DNS=8.8.8.8 <<<<<<<<<<<<<< 追記
GATEWAY=192.168.1.1 <<<<<<< 追記
IPADDR=192.168.0.6
NAME=enp0s3
NETMASK=255.255.255.0
ONBOOT=yes
TYPE=Ethernet
--------------------------
```

- 参考URL
  - https://qiita.com/ponsuke0531/items/7e69155e1a2258d444c9
