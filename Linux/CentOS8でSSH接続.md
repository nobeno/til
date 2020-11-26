## CentOS8でSSH接続

- root以外ユーザーのユーザーを作成して、sudoコマンド実施権限を与える

- パッケージ最新化
  - `sudo dnf -y update`
  
- Firewall設定
  - sshd用のportxxxx追加：`sudo firewall-cmd --add-port=xxxx/tcp --zone=public`
  - ポート会報状況確認：`firewall-cmd --list-all`
  - 永続化：`sudo firewall-cmd --add-port=xxxx/tcp --zone=public --permanent`
  
- SElinux設定
  - 設定：`sudo dnf install -y policycoreutils-python-utils`
  - 設定：`sudo semanage port -a -t ssh_port_t -p tcp 4321`
  
- sshdの設定と起動
  - 起動：`sudo systemctl start sshd`
  - ファイル変更：`vi /etc/ssh/sshd_config` → `Port xxxx `を追加
  - 再起動：`sudo systemctl restart sshd`
  - 自動起動設定：`sudo systemctl enable sshd`
  
  - 参考：https://ubiqlog.com/archives/13588
