## S3+CloudFront構成におけるSignatureDoesNotMatchError

### 経緯
- S3+CloudFront+Route53で静的Webサイト公開
- アクセスするとSignatureDoesNotMatchError
- 変更したこと
  - リアルタイムログ取得のためOrigin Request Policy変更した
  - リアルタイムログ取得テストできたので、リアルタイムログ取得解除

### 原因
- Origin Request Policyにおいて、「Managed-AllViewer」を設定

### 解決方法
- Origin Request Policyを新たに作成
- Origin request contentsをすべて「None」に設定

### 参考
https://stackoverflow.com/questions/59431476/aws-s3-signaturedoesnotmatch-error-during-get-request-through-cloudfront
