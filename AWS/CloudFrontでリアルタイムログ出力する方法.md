### CloudFrontでリアルタイムログ出力す方法

#### CloudFrontリアルタイムログ
- リアルタイムにログを収集できる
- HTTPヘッダーの取得ができる
- 使用する場合、CloudFront＋Kinesisで費用が発生する

#### CloudFrontリアルタイムログ設定方法
1. Kinesis Date Streamsを作成する
  - US East Regionに作成する
  - シャード数を決める

2.CloudFrontリアルタイムログを設定する
  - ログに含めるフィールドを決める
  - サンプリングレートを決める（1~100,Kinesisに送信するビューワーリクエストの割合）

3.Kinesis Date Firehouseを作成する
  - Source元に作成したKinesis Date Streamsを選択する
  - ログを送信する先を選択する（例：S3）

#### 参考
- https://docs.aws.amazon.com/ja_jp/AmazonCloudFront/latest/DeveloperGuide/real-time-logs.html
- https://dev.classmethod.jp/articles/cloudfront-support-real-time-log/
