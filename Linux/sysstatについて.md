## syssyatについて

### sysstatとは
- Linux用サーバの負荷を分析するための監視ツール
- CPU負荷、ディスクI/O使用率、メモリ使用状況、ネットワークデバイス状況を調査できる
- sysstatパッケージに含まれるコマンド：sar・sadc・sadf・iostat・tapestat・cifsiostat・mpstat・pidstat

### インストール
```
[root@cent8 ~]# yum install -y sysstat
[root@cent8 cron.d]# sar -V
sysstat バージョン 11.7.3
(C) Sebastien Godard (sysstat <at> orange.fr)
```

### CentOS8/RHEL8設定ファイル
- sa設定ファイル
```
[root@cent8 /]# cat /usr/lib/systemd/system/sysstat-collect.timer
~~省略~~
HISTORY=3 # <=保存期間

# Compress (using xz, gzip or bzip2) sa and sar files older than (in days):
COMPRESSAFTER=31
~~~~~~~

```
- 記録間隔変更
```
[root@cent8 /]# cat /usr/lib/systemd/sysstat-collect.service
cat: /usr/lib/systemd/sysstat-collect.service: そのようなファイルやディレクトリはありません
[root@cent8 /]# cat /usr/lib/systemd/system/sysstat-collect.timer
# /usr/lib/systemd/system/sysstat-collect.timer
# (C) 2014 Tomasz Torcz <tomek@pipebreaker.pl>
#
# sysstat-11.7.3 systemd unit file:
#        Activates activity collector every 10 minutes

[Unit]
Description=Run system activity accounting tool every 10 minutes

[Timer]
OnCalendar=*:00/5 # <= 5分毎

[Install]
WantedBy=sysstat.service
```


### コマンド
- sar:システムの稼働状況を確認できるコマンド
- vmstat:メモリ・SWAP・ディスクI/O・CPU使用率を確認できるコマンド
- mpstat:CPU利用状況を確認できるコマンド
- コマンド実行例
```
[root@cent8 /]# sar
Linux 4.18.0-193.28.1.el8_2.x86_64 (cent8.nobeno.local) 	2020年12月10日 	_x86_64_	(1 CPU)

20:51:30     LINUX RESTART	(1 CPU)

20時55分10秒     CPU     %user     %nice   %system   %iowait    %steal     %idle
21時00分10秒     all      0.02      0.00      0.19      0.00      0.00     99.79
平均値:      all      0.02      0.00      0.19      0.00      0.00     99.79

[root@cent8 /]# vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 2  0      0 1406608   3276 308808    0    0   165    29   70  138  1  1 99  0  0
 
[root@cent8 /]# mpstat
Linux 4.18.0-193.28.1.el8_2.x86_64 (cent8.nobeno.local) 	2020年12月10日 	_x86_64_	(1 CPU)

21時05分12秒  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest  %gnice   %idle
21時05分12秒  all    0.59    0.04    0.27    0.06    0.20    0.04    0.00    0.00    0.00   98.79
```

### 参考
- https://beyondjapan.com/blog/2017/04/investigate-the-server-with-sysstat/
- https://tech-lab.sios.jp/archives/18604
