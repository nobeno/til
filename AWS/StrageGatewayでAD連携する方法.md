### StrageGatewayでAD連携する方法.md

#### 参考手順
- [【AWS StorageGateway】ファイルゲートウェイで簡単マウント/簡単アクセス制御](https://base.terrasky.co.jp/articles/WI3QN)
- [AWS StrageGatewayドキュメント](https://docs.aws.amazon.com/ja_jp/storagegateway/latest/userguide/create-gateway-file.html#GettingStarted-service-endpoint-file)

#### 上記の手順に合わせて必要な設定
- VPCエンドポイントの作成(インターネットを介さない場合)
  - Gateway用のEC2からStrageGatewayにアクセスするためのVPCエンドポイント
  - [Activating a gateway in a virtual private cloud](https://docs.aws.amazon.com/ja_jp/storagegateway/latest/userguide/gateway-private-link.html)
  
- DNS設定
  - DNSの設定をActiveDirectoryに変更する
  - [ファイルゲートウェイのDNS設定変更](https://nopipi.hatenablog.com/entry/2019/12/06/022719#i-%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%B2%E3%83%BC%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A4%E3%81%AEDNS%E8%A8%AD%E5%AE%9A%E5%A4%89%E6%9B%B4)
