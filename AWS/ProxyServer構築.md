## ProxyServer構築

### ProxyServer構築
- EC2(AmzonLinux2)インスタンスを起動
- Squidインストール：`sudo yum -y install squid`
- 設定記述：`sudo vi /etc/squid/squid.conf`
```
#
# 59行目あたりのhttp_access deny allよりも先に記述
# 49行目あたりから始まるINSERT YOUR OWN RULE(S)注釈以下に書いておくと分かりやすいかもしれない
#
# Squidを使用する自宅PCのIPアドレス
acl myacl src 111.222.333.444/32
# 自宅PCのアクセス許可
http_access allow myacl
#
# 64行目あたりに既に記載されている
# Squidで使用するポート番号、デフォルト値は3128
#
http_port 3128 
#
# 以下、アクセス元の匿名性を上げる処理を記述
#
# Proxyサーバのホスト名を擬態
visible_hostname unknown
# アクセス先に自宅PCのIPアドレスを知られないようにする
forwarded_for off
# ヘッダ情報出力抑制
request_header_access X-Forwarded-For deny all
request_header_access Via deny all
request_header_access Cache-Control deny all
#
# ログの出力。記述してもしなくてもOK
#
logformat combined %>a %<la %ui %un [%tl] "%rm %ru HTTP/%rv" %>Hs %<st "%{Referer}>h" "%{User-Agent}>h" %Ss:%Sh
access_log /var/log/squid/access.log combined
```
- 再起動:`sudo systemctl restart squid`
- 自動起動:`sudo systemctl enable squid`
- セキュリティグループにSquidポート許可

### EC2プロキシ設定
- 環境変数
```
export HTTP_PROXY=http://10.15.20.25:1234
export HTTP_PROXY=http://proxy.example.com:1234
export HTTPS_PROXY=http://10.15.20.25:5678
export HTTPS_PROXY=http://proxy.example.com:5678
export NO_PROXY=169.254.169.254
```
- Basic認証
```
export HTTP_PROXY=http://username:password@proxy.example.com:1234
export HTTPS_PROXY=http://username:password@proxy.example.com:5678
```

### 参考
- [AWS EC2にプロキシサーバを構築して海外向けサイトを国内から閲覧する](https://haloechoes.com/server-operations/build-proxy-servers-for-overseas-sites/)
- [HTTP プロキシを使用する](https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/cli-configure-proxy.html)
