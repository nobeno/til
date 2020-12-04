## netcatについて

### netcatとは
- TCPもしくはUDP接続などを利用して、コマンドラインからデータを送受信するためのツール

### インストール
- `$ dnf install nmap`
- `$ ncat --version`

### 利用方法
- nc <接続先ホスト>　<ポート番号>で利用
- TCPソケットの使い方
```
[サーバ側]
[root@server ~]# nc -kl 11111

# もう１つターミナルを開いて下記を実行
[root@server ~]# lsof -i4:11111 -P
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
nc      1433 root    4u  IPv4  26753      0t0  TCP *:11111 (★LISTEN)

[クライアント側]
[root@client ~]# nc server 11111

# TCPコネクションが確立された状態で、クライアントからサーバにデータを送信して、受信できるか確認
```

### 参考
- http://www.intellilink.co.jp/article/column/security-net01.html
- https://qiita.com/hana_shin/items/97e6c03ac5e5ed67ce38
