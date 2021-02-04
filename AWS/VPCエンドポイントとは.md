## VPCエンドポイントとは

### 2種類のVPCエンドポイントがある
- ゲートウェイ型： S3とDynamoDBが対応している
- インターフェース型： 50種類以上のサービスで対応している

### ゲートウェイ型
サポートされる AWS のサービスを宛先とするトラフィックのルートテーブルで、ルートのターゲットとして指定するゲートウェイ

### インターフェース型
サポートされるサービスを宛先とするトラフィックのエントリポイントとして機能するサブネットの IP アドレス範囲のプライベート IP アドレスを持つ Elastic Network Interface

### ドキュメント
https://docs.aws.amazon.com/ja_jp/vpc/latest/userguide/endpoint-services-overview.html
