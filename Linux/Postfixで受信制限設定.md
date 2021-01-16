## Postfixで受信制限設定

- 設定追記
```bash
[root@~]$ vi /etc/postfix/access
xxx.xxx@gmail.com OK
aaa.aaa@docomo.ne.jp OK

[root@~]$ vi /etc/postfix/main.cf
~
# white list
smtpd_sender_restrictions = check_sender_access hash:/etc/postfix/access,reject
~
```

- 設定反映
```bash
[root@~]$ postmap /etc/postfix/access
[root@~]$ systemctl restart postfix
```
