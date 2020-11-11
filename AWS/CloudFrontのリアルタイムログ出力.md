### CloudFrontのリアルタイム出力

- 手順
  1. Kinesis Date Stream を作成する
  2. Kinesis Firehose を作成する（ログ保存先をS3にする）
  3. CloudFrontのReal-time-logを設定する
  
  
- 費用が発生するもの
  - CloudFrontリアルタイムログ
  - Kinesis
  - ログ保管用S3


#### 参考
- [Amazon CloudFront でリアルタイムなログ出力が可能になりました](https://dev.classmethod.jp/articles/cloudfront-support-real-time-log/)
- [リアルタイムログ出力をサポートしたCloudFrontを試してみた](https://dev.classmethod.jp/articles/cloudfront-realtimelogs/)
