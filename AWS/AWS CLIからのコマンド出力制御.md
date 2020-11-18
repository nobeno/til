### AWS CLIからのコマンド出力制御

#### 出力形式
- コマンド：`--output`
  - json：デフォルト
  - yaml：バージョン2より対応
  - text
  - table

#### フィルタリング
- コマンド：`--query`
- 例：`aws ec2 describe-volumes --query 'Volumes[*].{ID:VolumeId,AZ:AvailabilityZone,Size:Size}'`


#### ドキュメント：https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/cli-usage-output.html
