## SWAPについて


#### SWAP領域とは
- ハードディスク内に設置される領域
- メモリー容量が足りなくなった時、メモリの中で不要な部分をSWAP領域に移動させる（スワップアウト）
- ハードディスクへのアクセスは遅いため、スワップアウトが多発するとパフォーマンス低下につながる

#### SWAP領域の確認
```
[root@cent8 ~]# free -m
              total        used        free      shared  buff/cache   available
Mem:           1827         154        1446           8         226        1520
Swap:          2095           0        2095
[root@cent8 ~]# cat /etc/fstab 

#
# /etc/fstab
# Created by anaconda on Tue Nov 24 07:39:10 2020
#
# Accessible filesystems, by reference, are maintained under '/dev/disk/'.
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
#
# After editing this file, run 'systemctl daemon-reload' to update systemd
# units generated from this file.
#
/dev/mapper/cl-root     /                       xfs     defaults        0 0
UUID=86c14804-3a2f-4208-823a-f51e25b5f2bb /boot                   ext4    defaults        1 2
/dev/mapper/cl-swap     swap                    swap    defaults        0 0

```

#### SWAP領域の作成
```
[root@cent8 ~]# sudo /bin/dd if=/dev/zero of=/var/swap.1 bs=1M count=1024
1024+0 レコード入力
1024+0 レコード出力
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 1.40094 s, 766 MB/s
[root@cent8 ~]# sudo /sbin/mkswap /var/swap.1
mkswap: /var/swap.1: パーミッション 0644 は安全な値ではありません。 0600 をお勧めします。
スワップ空間バージョン 1 を設定します。サイズ = 1024 MiB (1073737728 バイト)
ラベルはありません, UUID=8ce85e99-36b3-4cc8-81d4-912068ebde06

```


#### SWAP領域の有効化
```
[root@cent8 ~]# sudo /sbin/swapon /var/swap.1
swapon: /var/swap.1: パーミッション 0644 は安全な値ではありません。 0600 をお勧めします。
[root@cent8 ~]# swapon -s
ファイル名				タイプ		サイズ	使用済み	優先順位
/dev/dm-1                              	partition	2146300	0	-2
/var/swap.1                            	file    	1048572	0	-3
[root@cent8 ~]# free -m
              total        used        free      shared  buff/cache   available
Mem:           1827         155         417           8        1254        1518
Swap:          3119           0        3119
```


#### SWAP領域の削除
```
[root@cent8 ~]# swapoff -v /dev/dm-1 
スワップ /dev/dm-1 を無効化しています
[root@cent8 ~]# rm /dev/dm-1 
rm: ブロックスペシャルファイル '/dev/dm-1' を削除しますか? y
```


#### 参考URL
- https://www.wakuwakubank.com/posts/685-linux-swap/
- https://access.redhat.com/documentation/ja-jp/red_hat_enterprise_linux/7/html/storage_administration_guide/s1-swap-removing
