### SELinuxとfirewalld

- SELinuxとは
  - 事後防衛的なアクセス制御
  - 参考 : https://eng-entrance.com/linux-selinux
  - 確認コマンド : `getenforce`
  - 無効化 : 
    ``` 
    vi /etc/selinux/config 
    SELINUX=disable <=追加
    ```
    
- firewalldとは
  - CentOS 7から採用された「パケットフィルタリング」の仕組み
  - ルールに基づいて通信の許可／拒否を制御する、セキュリティ対策
  - 参考 : ルールに基づいて通信の許可／拒否を制御する、セキュリティ対策 
  - 確認コマンド : `systemctl status firewalld`
  - 無効化 : 
    ```
    systemctl stop firewalld
    systemctl disabled firewalld
    reboot
    ```
