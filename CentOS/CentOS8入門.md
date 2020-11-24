## CentOS8

#### CentOS7との違い
- パフォーマンス向上
- パッケージ管理がyumからdnfへ変更
- ファイヤーウォール昨日がiptablesからnftablesへ変更
- 時刻同期がchronyに一本化
- RHEL8 の標準設定では、TLS 1.0・TLS 1.1 をサポートしない状態
- yumコマンドは、dnfコマンドへのシンボリックリンクになっているため、dnfコマンドとyumコマンドは同じ結果になる

#### 構築参考URL
https://www.rem-system.com/centos-linux8-install/
