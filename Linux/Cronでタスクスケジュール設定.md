## Cronでタスクスケジュール設定

### スケジュール設定
- 設定コマンド：`crontab [-u ユーザー] { -e | -l | -r }`
  - -u: 指定したユーザーのcrontabファイルを操作
  - -l: crontabファイルの内容を表示
  - -r: crontabファイルを削除
  - -e: crontabファイルを編集
  - ユーザー指定なしの場合、設定したユーザーになる
  
<br>

- ファイル書式
```
# コメント
分　時　日　月　曜日　コマンド
```

<br>

- 設定例
```bash
[centos@ip-10-0-0-29 ~]$ crontab -e
# test
05 10 * * sun sudo reboot now
~
[centos@ip-10-0-0-29 ~]$ sudo systemctl restart crond
```

<br>

- 確認
```bash
[centos@ip-10-0-0-29 ~]$ systemctl status crond
[centos@ip-10-0-0-29 ~]$ vi /var/log/cron
```


### 参考
- https://webbibouroku.com/Blog/Article/centos-cron
- https://time4vps.ysklog.net/cron.html
