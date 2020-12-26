## syslogとは

- 稼働しているプログラムのログを、効率的に収集し記録するのがsyslog
- もともとはプロトコル（ルール）の一つで、他のコンピューター機器にログを送信する規格
- ログデータのある場所
  - プログラムが出力するログ（/var/log）
  - 各プログラムが出力するログの設定ファイル（.confファイル）
  - /etc/rsyslog.conf
- 設定ファイルrsyslog.confについて
  - `vi /etc/rsyslog.conf`:「MODULES」「GLOBAL DIRECTIVES」「RULES」の3部構成
  - `systemctl restart rsyslog`:更新したら反映させる
- 参考
  - https://www.kagoya.jp/howto/cloud/syslog/
