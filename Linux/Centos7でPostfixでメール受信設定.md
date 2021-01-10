## Centos7でPostfixでメール受信設定

### Postfix install
- CentOS7には基本インストール済みである
```
[root@ip-10-0-0-29 ~]# yum list installed | grep postfix

postfix.x86_64                             2:2.10.1-9.el7             installed
[root@ip-10-0-0-29 ~]#
[root@ip-10-0-0-29 ~]# yum -y update postfix
```

### Postfixコンフィグ設定
- `inet_interfaces`と`mydestination`の設定だけすれば、サーバ内に受信は可能
- 参考：[postfixで外部からメールを受信できるようにする](http://co-akuma.directorz.jp/blog/2010/03/postfix%e3%81%a7%e5%a4%96%e9%83%a8%e3%81%8b%e3%82%89%e3%83%a1%e3%83%bc%e3%83%ab%e3%82%92%e5%8f%97%e4%bf%a1%e3%81%a7%e3%81%8d%e3%82%8b%e3%82%88%e3%81%86%e3%81%ab%e3%81%99%e3%82%8b/)
```
[root@ip-10-0-0-29 postfix]# vi main.cf
---
#myhostname = host.domain.tld
→myhostname = <サブドメイン名> 

#mydomain = domain.tld
→mydomain = <ドメイン名>

#inet_interfaces = all
inet_interfaces = localhost
→inet_interfaces = all
#inet_interfaces = localhost

mydestination = $myhostname, localhost.$mydomain, localhost
#mydestination = $myhostname, localhost.$mydomain, localhost, $mydomainmynetworks_style = host
→#mydestination = $myhostname, localhost.$mydomain, localhost
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain

#home_mailbox = Maildir/
→home_mailbox = Maildir/
---
〜
[root@ip-10-0-0-29 postfix]# postconf -n　　←main.cfで読み込まれるパラメータを確認
〜
[root@ip-10-0-0-29 postfix]# systemctl restart postfix
[root@ip-10-0-0-29 postfix]# systemctl status postfix
```

### AWS上に構築する場合の設定
- Aレコード

| Key | Value |
---- | ----  
| ルーティングポリシー | シンプルルーティング |
| レコード名 | 任意のサブドメイン名 ex) mail.example.com |
| 値/トラフィックのルーティング先	| smtp-serverのPublicIPアドレス |
| レコードタイプ | A |

<br/>

- MXレコード

| Key | Value |
---- | ----  
| ルーティングポリシー | シンプルルーティング |
| レコード名 | ドメイン名 ex) example.com |
| 値/トラフィックのルーティング先	| 10 "Aレコードに登録したサブドメイン" ex) 10 mail.example.com |
| レコードタイプ | MX |

<br/>

- セキュリティグループ
  - Inbound	SMTP:0.0.0.0/0

### 参考
- https://blog.serverworks.co.jp/build-smtp-server
- https://qiita.com/takahashi-kazuki/items/6ab499d53d6d62919a37
